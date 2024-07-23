# 2. React Hooks

**前言：**

掌握 React 中的关于生命周期的概念：

简单来说就是程序运行到特定阶段会运行的方法

![img](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405021607121.webp)

挂载

- constructor
- getDerivedStateFromProps
- render
- componentDidMount

更新

- getDerivedStateFromProps
- shouldComponentUpdate
- render
- getSnapshotBeforeUpdate
- componentDidUpdate

卸载

- componentWillUnmount



**简单来说：**

初次加载时顺序： constructor  >>  render  >> componentDidMount

数据更新后顺序： render >> componentDidUpdate

卸载时： componentWillUnmount（程序关闭时触发 **Will**）

------

## 2.1 useState

### 基本用法

让函数式组件拥有自己的状态，进行状态数据的初始化、读取、更新。

```jsx
// const [状态名, set函数] = useState(初始值)
const [data, setData] = useState(1)
```



```jsx
import {useState} from 'react'

export default function Count() {
    const [data, setData] = useState(0)
    
    return(
    	<>
        	<button onclick={() => {setData(data + 1)}}> +1 </button>
        </>
    )
}
```

函数式组件的渲染就是执行函数，当组件状态发生改变后，React会重新执行组件函数进行重新渲染。

根据最新的状态 return 最新的DOM结构

**注：当组件函数进行重新渲染时，不会重复执行useState函数赋值数据，而是拿上次的state值**



### 以函数形式为状态赋初值：

格式：

```jsx
const [data, setData] = useState(() => 初始值)
```

例如：

```jsx
export default DateCom() {
    const [date, setDate] = useState(() => {
        const dt = new Date()
        return {
            year: dt.getFullYear(),
            month: dt.getMonth() + 1,
            day: dt.geDate()
        }
    })
    
    return (
        <>
        <h1>今日信息：</h1>
        <p>年份：{date.year}</p>
        <p>月：{date.month}</p>
        <p>日：{date.day}</p>
        </>
    )
}
```

### useState是异步更新状态

调用useState() 返回一个变更状态的函数，这个函数是以异步的形式修改状态的，所以修改状态后无法立即拿到最新的状态，例如：

```jsx
function App() {
  const [count, setCount] = useState(0)

  function add() {
    setCount(count + 1)

    console.log(count)
  }

  return (
    <>
      <div style={{marginLeft:450,marginTop:300}}>
        <h1>当前的Count: {count}</h1>
        <button style={{backgroundColor:'lightblue' ,borderRadius:12, width:50, padding:8, margin:10}} onClick={add}>
           +1 
        </button>
      </div>
    </>
  )
}
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405031538958.png" alt="image-20240503153856894" style="zoom:50%;" />

当add执行后进行打印仍然得到是上一次的state

**useEffct监听改变并执行回调函数**

语法：

```jsx
useEffect(() => {}, [依赖项])
```

例如：

```jsx
function App() {
  const [count, setCount] = useState(0)

  function add() {
    setCount(count + 1)
  }
    
  useEffect(() => {
      console.log(count)
  },[count])

  return (
    <>
      <div style={{marginLeft:450,marginTop:300}}>
        <h1>当前的Count: {count}</h1>
        <button style={{backgroundColor:'lightblue' ,borderRadius:12, width:50, padding:8, margin:10}} onClick={add}>
           +1 
        </button>
      </div>
    </>
  )
}
```

![image-20240503155406412](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405031554456.png)

###  更新对象类型的值



**如果要更新对象类型的值并进行组件的重新渲染，需要展开运算符或者Object.assign({}，原对象)生成新对象，才能正常触发渲染。不能直接修改原对象的属性**

**因为set函数内部会对更新前后的值进行比较，如果引用相同则不进行重新渲染**

```jsx
function Userinfo() {
  
  const [user, setUser] = useState({
    name: 'wc',
    gender: 'male',
    age: 18
  })

  function update() {
    setUser({...user,age:20})
  }

  return (
    <>
      <h1>用户信息：</h1>
      <p>名字：{user.name}</p>
      <p>性别：{user.gender}</p>
      <p>年龄：{user.age}</p>
      <button onClick={update}> Update </button>
    </>
  )
}

export default Userinfo
```

###  强制刷新组件

原理就是useState导致组件状态发生改变后，React会重新执行组件函数进行重新渲染。

```jsx
export function Updatezj() {
  const [, forceUpdate] = useState({})

  function update() {
    forceUpdate({})
  }

  return (
    <>
      <button onClick={update}>刷新组件：{Date.now()}</button>
    </>
  )

}
```



##  2.2 useRef

useRef() 返回一个可变的ref对象，该对象只有一个current属性。可以在调用useRef函数时为其指定初始值，并且这个ref对象在整个生命周期内保持不变。

```jsx
const Objref = useRef(初始值)

console.log(Objref.current)
```

useRef()解决两个问题：

1.获取DOM元素或子组件的实例对象

2.存储渲染周期之间共享的数据

### 获取DOM元素

拿元素时一般传null

```jsx
export function Refuse() {

  const Objref = useRef(null)

  function gete() {
    Objref.current.focus()
    console.log(Objref.current)
  }

  return (
    <>
      <input type="text" ref={Objref} />
      <button onClick={gete}>获取焦点</button>
    </>
  )

}
```

![image-20240503173421545](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405031734592.png)

### 存储渲染周期之间的共享数据

就比如说使用useState时想同时拿更新前后的值进行操作，就需要useRef。

**同样的。useRef只有组件第一次渲染时执行创建对象，后面组件被更新重新渲染时不再执行。**

```jsx
export function DateRef() {

  const [count, setCount] = useState(0)

  const dataRef = useRef()

  function add() {
    setCount(c => c + 1)
    dataRef.current = count
  }

  return (
    <>
      <h1>当前值：{count},旧值：{dataRef.current}</h1>
      <button onClick={add}> +1 </button>
    </>
  )
}
```

![image-20240503175653429](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405031756458.png)



###  注意事项

**1. useRef只有组件第一次渲染时执行创建对象，后面组件被更新重新渲染时不再执行。**

**2. ref.current变化时不会造成组件的render**

```jsx
export function Refrender() {

  const [count,setCount] = useState(0)

  const refobj = useRef(Date.now())

  function add() {
    setCount(c => c + 1)
  }

  function updataref() {
    refobj.current = Date.now()
    console.log(refobj.current);
  }

  console.log('render components');

  return (
    <div style={{marginLeft:300,marginTop:300}}>
      <h1>current's count: {count} </h1>
      <h1>current's refdata: {refobj.current} </h1>
      <button onClick={add}> count +1 </button>
      <button onClick={updataref}> update refdata </button>
    </div>
  )
}
```

![image-20240503211508621](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405032115763.png)

**3. 由于useRef不会造成组件的重新渲染，React也不会追踪ref.current变化，因此ref.current不能作为其他Hooks的依赖项**

### forwardRef()

这是官方提供的一个Api，因为在useRef无法引用在组件上，组件不是一个实例，所以需要forwardRef()将子组件的DOM节点暴露给父组件。

```jsx
// props父组件传递的属性 + 转发过来的ref

const 组件名 = forwardRef((props, ref) => {})

or

forwardRef(function 组件名(props, ref) {})
```

例如：

```jsx
const Child = forwardRef((props, ref) => {
  const [count, setCount] = useState(0)

  function add(n) {
    setCount(c => c + n)
  }

  return (
    <>
      <div>
        <p>current count: {count}</p>
        <button onClick={() => add(1)}> +1 </button>
        <button onClick={() => add(-1)}> -1 </button>
      </div>
    </>
  )

})

export function Father() {

  const refChild = useRef()

  return (
    <>
      <div style={{marginLeft:250, marginTop:100}}>
        <h1>This is My Father components</h1>
        <hr />
        <Child ref={refChild} />
      </div>
    </>
  )
}
```

![image-20240503233929534](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405032339674.png)

------

### useImperativeHandle 按需暴露成员

**用于ref引用后在子组件中按需暴露成员**

```jsx
// 子组件
const Child = forwardRef((props, ref) => {
  const [count, setCount] = useState(0)

  function add(n) {
    setCount(c => c + n)
  }

  useImperativeHandle(ref, () => ({
    count,
    setCount
  }))

  return (
    <>
      <div>
        <p>current count: {count}</p>
        <button onClick={() => add(1)}> +1 </button>
        <button onClick={() => add(-1)}> -1 </button>
      </div>
    </>
  )

})
```

```jsx
// 父组件
export function Father() {

  const refChild = useRef()

  function reset() {
    refChild.current.setCount(0)
  }

  return (
    <>
      <div style={{marginLeft:250, marginTop:100}}>
        <h1>This is My Father components</h1>
        <button onClick={reset}> 重置Count </button>
        <hr style={{width:1000}} />
        <Child ref={refChild} />
      </div>
    </>
  )
}
```

### 控制成员暴露的粒度

在子组件中，我们希望暴露是一个重置count为0的函数，而不希望直接把setCount暴露出去，因为父组件调用setCount()可以传递任何的值，因此我们希望基于useImperativeHandle，向外提供一个reset()函数，写死传入的值。

```jsx
const Child = forwardRef((props, ref) => {
  const [count, setCount] = useState(0)

  function add(n) {
    setCount(c => c + n)
  }

  useImperativeHandle(ref, () => ({
    count,
    reset: () => setCount(0)
  }))

  return (
    <>
      <div>
        <p>current count: {count}</p>
        <button onClick={() => add(1)}> +1 </button>
        <button onClick={() => add(-1)}> -1 </button>
      </div>
    </>
  )

})

export function Father() {

  const refChild = useRef()

  function reset() {
    refChild.current.reset()
  }

  return (
    <>
      <div style={{marginLeft:250, marginTop:100}}>
        <h1>This is My Father components</h1>
        <button onClick={reset}> 重置Count </button>
        <hr style={{width:1000}} />
        <Child ref={refChild} />
      </div>
    </>
  )
}
```

### useImperativeHandle 第三个参数

```jsx
useImperativeHandle(ref, createHandle, [deps])
```

`1` ref： 为父组件传递的ref

`2 ` createHandle：该参数为函数，返回的对象自动绑定到ref上

`3` deps：函数的依赖项，可选。若 createHandle 函数中用到了子组件内部定义的变量，则还需要将该变量作为依赖变量成为 useImperativeHandle 的第三个参数

第三个参数有3种用法：

**1. 空数组[]**： **只有子组件首次渲染时，执行useImperativeHandle中的fn回调**，从而把return的对象作为父组件接收到的ref。

**2. 存在依赖项[deps]**：[deps]每次变化时，都会重新执行回调，return新的对象

**注意：如果子组件存在多个useState，虽然组件状态改变会引起组件重新渲染，但是useImperativeHandle有依赖项时只被依赖项影响，并不会因为其他状态改变渲染导致其回调重新执行返回对象。**

**3. 省略依赖项**：组件内**任何一个useState状态改变**都会导致**useImperativeHandle的回调重新执行**

------

## 2.3 useEffect

函数副作用：就是函数**除了返回值**外对外界环境的**其他影响**，即与渲染无关的操作。例如**获取数据**、**修改全局变量**、**更新DOM**等。

语法：

```jsx
useEffect(fn, deps?)
```

其中，

-第一个参数fn是一个副作用函数，该函数会在**每次渲染完成后**被调用

-第二个参数是**可选依赖项数组**，这个数组每一项内容都会被用来进行**渲染前后的对比**

​	依赖项变化：重新执行fn

​	依赖项不变：不执行fn

### 执行时机

一般来说，useEffect会在组件每次渲染完成后执行。例如：

**省略deps**

```jsx
// 省略了依赖项数组

export function Effectuse() {
  const [count, setCount] = useState(0)

  function add() {
    setCount(c => c + 1)
  }

  useEffect(() => {
    console.log(document.querySelector('h1').innerText)
  })

  return (
    <>
      <h1>Count value: {count}</h1>
      <button onClick={add}> +1 </button>
    </>
  )
}
```

![image-20240504160457219](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405041604375.png)



**deps为依赖项**

1.空数组

只在组件**首次渲染完成后执行一次**

![image-20240504160910856](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405041609900.png)

2.数组存在值

**只有依赖项数组内的值改变**，React跟踪到了就会在渲染完成后重新执行useEffect的fn

依赖项**不建议使用对象**，因为React使用Object.is()判断

### useEffect注意事项

1.不要在useEffect内改变依赖项的值，会造成死循环

2.多个功能不同的副作用尽量分开，不要写在一个useEffect中

### 如何清理副作用

useEffect 可以返回一个函数，用于清理副作用的回调。

**React会判断useEffect 有没有return一个函数，有的话当再次执行useEffect时先将return的函数执行了再执行useEffect，还有卸载时也会执行return的函数**

**总结：**

1.useEffect当**没有依赖项**时，组件**每次渲染后执行useEffect**，如果因为useEffect里改变了组件的State，所以组件在一直重复渲染，当有return的函数时，每次useEffect执行前**先执行return的函数**再执行useEffect内容。

![image-20240504221530040](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405042215129.png)

2.useEffect有**空数组依赖项**时，组件在**渲染完成后执行useEffect**，当有return的函数时，只有卸载时执行，因为只渲染一次后不再重新渲染，组件卸载再加载等价于首次加载组件不会执行return的函数。

![image-20240504222534060](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405042225116.png)

**等于说，首次执行渲染时都不执行return的函数，卸载时一定执行return的函数，其他看情况，只要Effect被重新执行，那return函数先执行。**

语法：

```jsx
useEffect(() => {
    // 执行副作用操作
    // 返回清理函数
    return () => { 写清理操作 }
}, [deps])
```

例如：

```jsx
function Mouseevent() {
  const [position, setPosition] = useState({x: 0,y: 0})

  useEffect(() => {
    function mousem(e) {
      console.log(e.clientX, e.clientY)
      setPosition({x: e.clientX,y: e.clientY})
    }

    console.log('Effect执行了');

    window.addEventListener('mousemove', mousem)

    return () => {
      console.log('卸载了');
      window.removeEventListener('mousemove', mousem)}
  },[])

  return (
    <>
      <h4>Mouse location: {JSON.stringify(position)}</h4>
    </>
  )
}


export function Mouseinfo() {

  const [flag, setFlag] = useState(true)

  return (
    <>
      <button onClick={() => setFlag(f => !flag)}>Toggle</button>
      <hr />
      {flag && <Mouseevent />}
    </>
  )
}
```

**为上面鼠标事件加截流操作，提高性能**

```jsx
useEffect(() => {
    let timeid
    function mousem(e) {
      if(timeid !== undefined) return
      timeid = setTimeout(() => {
        console.log(e.clientX, e.clientY)
        setPosition({x: e.clientX,y: e.clientY})
        timeid = undefined
      },500)
    }

    console.log('Effect执行了');

    window.addEventListener('mousemove', mousem)
    
    return () => {
      console.log('卸载了');
      window.removeEventListener('mousemove', mousem)}
  },[])
```



## 自定义秒数倒计时Hooks

**Hooks本质就是函数组件**，所以编写可复用的通用的函数式组件 === Hooks，注意**命名以use开头**。

最后将需要的**方法和属性return**出去即可。

功能分析：

1.用户调用useCountDown(),可以传入参数指定倒计时秒数，不传默认为10s

2.对用户传递参数进行非法处理

3.每隔1秒让秒数-1，并使用bool记录按钮是否被禁用

4.以数组形式，向外返回每次的秒数和当前的禁用状态，例如return [count, disabled]

```jsx
export function CountDown(num) {
  
  if(typeof num !== Number) {
    
  }

  const [count, setCount] = useState(num)

  const [flag, setFlag] = useState(true)

  useEffect(() => {
    const timeId = setTimeout(() => {
      if(count > 1) {
        setCount(c => c - 1)
      }else {
        setFlag(!flag)
        clearTimeout(timeId)
      }
    }, 1000)

    return () => clearTimeout(timeId)
  },[count])

  return (
    <>
      <button disabled={flag} onClick={() => console.log('协议ojbk')}>{flag ? `请阅读此协议（${count}s）` : `同意此协议`}</button>
    </>
  )
}
```

## 2.4 useReducer

类似useState也是对状态进行管理，不过useState过多时会变得难以管理，而useReducer可以进行复杂的状态管理。而且useReducer进行的状态管理可以抽离于组件。

语法：

```jsx
const [state, dispatch] = useReducer(reducer, initState, initAction?)
```

![image-20240506184436305](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405061844418.png)

**调用dispatch触发reducer返回新状态**

**通过useReducer管理的状态不能直接通过state进行修改，虽然能修改，但是React不监听，修改后组件不会刷新。，只能通过reducer函数接收旧状态返回新状态。**

dispatch(信息对象)

例如：dispatch({type: 'UPDATE_NAME', payload: 'wangcai'})

reducer(prevstate, action) action就是dispatch传递的信息对象

```jsx
const reducer = (prevState, action) => {
  switch(action.type) {
    case 'add' :
      return {...prevState, age: prevState.age + 1}

    default:
      return prevState
    }
  }


const initAction = (initState) => {
  return {...initState, 
          age: Math.round(Math.abs(initState.age)) || 18
  }
}

const initState = {
  name: 'wc',
  age:-18
}

export function Reducers() {

  const [state, dispatch] = useReducer(reducer, initState, initAction)
  
  
  return (
    <>
      <h2>Current state: {JSON.stringify(state)}</h2>
      <button onClick={() => dispatch({type: 'add', payload: 1})}>age : +1 </button>
    </>
  )
}
```



因为reducer里的case每次都要return {...prevState}，为了减少工作量，可以使用immer

**npm i immer use-immer -S**

**使用useImmerReducer函数即可，对应的case下直接修改对应属性后break即可，无需return和解构原旧值**



## 2.5 useContext

父组件想把数据共享给深层子组件时，传统方法是props一层一层传递，可维护性太差。

我们可以使用React.createContext() + useContext()实现多层组件的数据传递

![image-20240506204626506](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405062046679.png)

```jsx
const MyContext = createContext({})

export function Die() {
  return (
    <>
      <MyContext.Provider value={{name: 'wc', age: 18}}>
        <Erzi></Erzi>
      </MyContext.Provider>
    </>
  )
}

const Erzi = () => {
  const ctx = useContext(MyContext)

  return (
    <>
      <h2>My Name: {ctx.name}</h2>
      <h3>age: {ctx.age}</h3>
    </>
  )
}
```



![image-20240511141035218](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202405111410291.png)













































