# React UI Library 
## Semantic-UI Library

### Import Library
- lodash.js
    - [공식 페이지](https://lodash.com/, "공식페이지")
    > A modern JavaScript utility library delivering modularity, performance & extras.
    - FP 패러다임에서 쓰이는 
    일반적인 프로그래밍 작업을 위한 유틸리티 함수 라이브러리
    (출처 : [wikipedia](https://en.wikipedia.org/wiki/Lodash "Wikipedia"))
- classnames.js
    - [공식 페이지](  http://jedwatson.github.io/classnames
)
    > A simple javascript utility for conditionally joining classNames together
    - class 이름을 합쳐주는 library
    - true, false 로 class 를 조정할 수 있음
    ~~~
    const classes = cs('foo', { bar: true }); // foo, bar
    const classes = cs('foo', { bar: false }); // foo
    ~~~
- prop-types
    - [공식 페이지](https://www.npmjs.com/package/prop-types)
    > Runtime type checking for React props and similar objects.
    - 타입 체크 라이브러리

> 위 라이브러리를 잘 이용하면 좋겠음

### Header
#### props
- 종류 : attached, block, children, className, color, content, disabled, dividing, floated, icon, image, inverted, size, sub, subheader, textAling

#### class
- 종류 : ui, color, size, block, disabled, dividing, floated, icon, image, inverted, sub, attached, textAling, header, className

#### rest
- getUnhandleProps
- 컴포넌트의 scope 을 벗어나는 props 를 return
#### ElementType
- getElementType
- createElement() 의 type을 return

#### return
- 3가지 타입
    - children != null
    - icon || image
    - default
- create element
    - icon Element
    - image Element
    - subheader Element

#### 주요함수
- getElementType
    ~~~
    function getElementType(Component, props, getDefault) {
    const { defaultProps = {} } = Component

    // 1. 사용자 정의 Element tag
    if (props.as && props.as !== defaultProps.as) return props.as
    
    // 2. getDefault 가 있을 때
    if (getDefault) {
        const computedDefault = getDefault()
    
        if (computedDefault) return computedDefault
    }

    // 3. Anchor link
    if (props.href) return 'a'

    // 4. defaultProp or DIV tag
    return defaultProps.as || 'div'
    }
    
    export default getElementType
    ~~~

- getUnhandledProps
    ~~~
    const getUnhandledProps = (Component, props) => {
    // Note that `handledProps` are generated automatically during build with `babel-plugin-transform-react-handled-props`
    const { handledProps = [] } = Component

    return Object.keys(props).reduce((acc, prop) => {
        if (prop === 'childKey') return acc
        if (handledProps.indexOf(prop) === -1) acc[prop] = props[prop]
        return acc
    }, {})
    }

    export default getUnhandledProps
    ~~~


    