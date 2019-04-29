---
title: 用ES6定义一个react组件
tags: React #此文章在`标签1 `标签下
#tags: [标签1,标签2] #此文章在`标签1,标签2`下
---
```
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title></title>
    <script src="https://cdn.bootcss.com/react/16.4.0/umd/react.development.js"></script>
    <script src="https://cdn.bootcss.com/react-dom/16.4.0/umd/react-dom.development.js"></script>
    <script src="https://cdn.bootcss.com/babel-standalone/6.26.0/babel.min.js"></script>
</head>

<body>
    <div id="root">


        <h1>
            <p>姓名: </p>
            <p>年龄: </p>
        </h1>
    </div>
</body>

</html>

<script type="text/babel">
    /**
        * es6使用class的形式来创建组件,继承React的Component类,
        * 后面我们更多的使用这种方式来创建组件
     */ 
    class Welcome extends React.Component {
        constructor(props) {
            super(props);
        }
        render() {
            return (
                <h1>
                    <p>姓名: {this.props.person.name}</p>
                    <p>年龄: {this.props.person.age} </p>
                </h1>
            )
        }
    }

    const person = {
        name: 'huruqing',
        age: 108
    }
    ReactDOM.render(
        <Welcome person={person} />,
        document.getElementById('root')
    )
</script>
```









