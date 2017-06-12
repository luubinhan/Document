10 React mini-patterns

# Truyền dữ liệu qua lại giữa component cha và con

![Worth a thousand words?](https://cdn-images-1.medium.com/max/2000/1*J5XOQh2WKIl0NFTAMvcVbQ.png)

Component con `ListOfThings` sẽ nhận dữ liệu từ component cha `App` thông qua `props.items`, hiển thị dữ liệu này, các thao tác xử lý dữ liệu của trên `props.items` cũng sẽ thực hiện trên component cha `App`.

Tách 2 component như thế này để 1 component chỉ chuyên để hiển thị, 1 component sẽ đảm nhận xử lý logic.

# Fix HTML input

![If I’m building a site that will have a lot of user inputs, one of the first things I do is fix this.](https://cdn-images-1.medium.com/max/800/1*WTUJjlFOOnetc5NpbykN0w.png)

# Tự động truyền giá trị `for` cho `label`

Ai lại đi tự động điền cập giá trị for/id cho từng label/input nhỉ. Một module đơn giản sẽ rất hữu ích

```js
class Input extends React.Component {
    constructor(props) {
        supper(props);
        this.id = getNextId();
        this.onChange = this.onChange.bind(this);
    }

    onChange(e) {
        this.props.onChange(e.target.value);
    }

    render(){
        return(
                <label for={this.id}>
                    {this.props.label}

                    <input>
                        id={this.id}
                        value={this.props.value}
                        onChange={this.onChange}
                    </input>
                </label>
            )
    }
}
```


module tự tạo tăng giá trị id

```js
let count = 1;

export const resetId = () => {
    count = 1;
}

export const getNextId = () => {
    return `element-id-${count++}`;
}
```


# Biến CSS với props

Với những component như button có nhiều style như primary, danger, info, default, hãy thử cách thông minh sau

```html
<Button theme="primary">Hello</Button>
```

thêm thuộc tính bo tròn nào, không cần rounded={true} luôn

```html
<Button theme="default" rounded>Hello</Button>
```

Thêm các thiết đặt khác

```html
<Icon width="25" height="25" type="search" />
```

Component như vậy sẽ được thiết kế như sau

```js
const Button = (props) => {
    let className = `btn btn-${props.theme}`;
  
    if (!props.rounded) className += ' btn-no-rounded';

    return <button className={className}>{props.children}</button>;
}
```

# Switch Component