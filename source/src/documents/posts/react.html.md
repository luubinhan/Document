React mini-patterns

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
    if (!props.rounded) className +=' btn-no-rounded';
    return(
        <button className={className}>{props.children}</button>;
    )
}
```

# Truy xuất tới component

Sử dụng khái báo `ref` trên component

```js
class Input extends React.Component{
    focus(){
        this.el.focus();
    }
    render() {
        return(
             <input ref={el => {this.el = el}} />
            )
    }
}
```

# Almost-components

Giờ build một component cho phép user input giá trị tìm kiếm, danh sách kết quả tương sẽ hiển thị ngay lập tức.

![(I’m searching for political satirists because I, like everyone, am super interested in what other people think about politics.)](https://cdn-images-1.medium.com/max/800/1*AH_RjXx3xldF651qvef7cQ.png)

Mỗi kết quả trả về không nhất thiết phải là một component mới, đơn giản hãy khai báo một phương thức trả về html

```js
const SearchSuggestions = (props) => {
  // renderSearchSuggestion() behaves as a pseduo SearchSuggestion component
  // keep it self contained and it should be easy to extract later if needed
  const renderSearchSuggestion = listItem => (
    <li key={listItem.id}>{listItem.name} {listItem.id}</li>
  );
  
  return (
    <ul>
      {props.listItems.map(renderSearchSuggestion)}
    </ul>
  );
}
```

Nếu nó không hẳn là một component, hãy tạo nó như một phương thức trong component cha.


# Component để định dạng

Đừng nghĩ component như một cái gì đó to lớn, đôi khi chỉ để định dạng một phần tử, che đi cấu trúc html


```js
const Price = (props) => {
    const price = props.children.toLocaleString('en', {
      style: props.showSymbol ? 'currency' : undefined,
      currency: props.showSymbol ? 'USD' : undefined,
      maximumFractionDigits: props.showDecimals ? 2 : 0,
    });
    
    return <span className={props.className}>{price}</span>
};

const Page = () => {
  const lambPrice = 1234.567;
  const jetPrice = 999999.99;
  const bootPrice = 34.567;
  
  return (
    <div>
      <p>One lamb is <Price className="expensive">{lambPrice}</Price></p>
      <p>One jet is <Price showDecimals={false}>{jetPrice}</Price></p>
      <p>Those gumboots will set ya back <Price showDecimals={false} showSymbol={false}>{bootPrice}</Price> bucks.</p>
    </div>
  );
};
```

# Import component không cần đường dẫn

Ác mộng khi phải import tất cả component kèm với đường dẫn của nó như thế này

```js
import Button from '../../../../Button/Button.jsx';
import Icon from '../../../../Icon/Icon.jsx';
import Footer from '../../Footer/Footer.jsx';
```

Tạo một file `index.js` đâu đó, export toàn bộ component
Sử dụng config trong webpack `resolve.alias` để chỉ đến file index

Cách này chưa sử dụng được với webpack 2, eslint báo lỗi component không nằm trong node_modules.

Mình sẽ update lại sau khi tìm ra cách làm cho vấn đề này.