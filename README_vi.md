**Thiếu phần Bouncing loader**

### Chỉnh lại Box-sizing
Chỉnh lại box-model để `width`s và `height`s không bị ảnh hưởng bởi `border` hoặc `padding` của nó(box-model).
#### CSS

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```


#### Giải thích
1. `box-sizing: border-box` làm phần tăng thêm của `padding` hoặc `border`s không ảnh hưởng đến `width` hoặc `height` của phần tử.
2. `box-sixing: inherit` làm một phần tử tuân theo `box-sizing` của cha nó.

#### Trình duyệt hỗ trợ
98.4%

<span class="snippet__support-note">✅ Không có cảnh báo nào.</span>

* https://caniuse.com/#feat=css3-boxsizing

### Clearfix
Đảm bảo là một phần tử tự clears các phần tử con của nó

#### Chú ý: Nó chỉ có tác dụng khi bạn vẫn đang sử dụng float để xây dựng layouts. Hãy xem xét việc sử dụng cách tiếp cận hiện đại với flexbox layout hoặc grid layout.

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

#### CSS

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.floated {
  float: left;
}
```

#### Giải thích 
1. `.clearfix::after` định nghĩa là một phần tử giả.
2. `content: ''` cho phép phần tử giả ảnh hưởng đến layout.
3. `clear: both` chỉ ra rằng hai phía tría phải của phần tử không thể liền kề với các phần tử float trước đó trong cùng 1 khối định dạng

#### Trình duyệt hỗ trợ
99+%

<span class="snippet__support-note">⚠️ 
Để phần này thực hiện đúng bạn cần đảm bảo rằng không có phần tử con không float nào trong container và không có phần float nào trước clearfixed container trong cùng định dạng (ví dụ như các cột float).</span> 

### Cố định tỉ lệ width với height 
Với mỗi biến width của một phần tử, nó sẽ đảm bảo height của phần tử đó vẫn theo tỉ lệ theo hình thức responsive (tỉ lệ height width vẫn giữ nguyên)
#### HTML

```html
<div class="constant-width-to-height-ratio"></div>
```

#### CSS

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```
#### Giải thích 
`padding-top` trong `::before` phần tử giả khiến height của phần tử luôn bằng một tỉ lệ phần trăm với width của nó. `100%` vì thế nghĩa là height của phần tử sẽ luôn bằng 100% width, tạo một khung responsive.

Phương pháp này cũng cho phép nội dung được đặt trong một phần tử bình thường.

#### Trình duyệt hỗ trợ
99+%

<span class="snippet__support-note">✅ Không có cảnh báo nào.</span>

### Phân phối đều các phần tử con
Phân phối đều các phần tử con bên trong một phần tử cha.

#### HTML

```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```

#### CSS

```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```
#### Giải thích
1. `display:flex` cho phép flexbox
2. `justify-content: space-between` phân bố đều các phần tử con theo chiều ngang. Item thứ nhất được đặt phía cạnh trái, trong khi item cuối cùng được đặt phía cạnh phải.

Cách khác, sử dụng `justify-content: space-around` để phân bố phần tử con với khoảng trắng bao quanh chúng, thay vì nằm giữa chúng.

#### Trình duyệt hỗ trợ
98.1%

<span class="snippet__support-note">⚠️ Cần tiền tố để hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=flexbox

### Flexbox centering

Đặt phần tử con ở trung tâm phần từ cha theo chiều ngang cũng như dọc sử dụng `flexbox`.
#### HTML

```html
<div class="flexbox-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Giải thích 
1. `display: flex` cho phép flexbox.
2. `justify-content: center` đặt phần tử con nằm ở trung tâm theo chiều ngang.
3. `align-items: center` đặt phần tử con nằm ở trung tâm theo chiều dọc.

#### Trình duyệt hỗ trợ
98.1%

<span class="snippet__support-note">⚠️ Cần tiền tố để hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=flexbox

### Grid centering
Đặt phần tử con ở trung tâm phần từ cha theo chiều ngang cũng như dọc sử dụng `grid`.

```html
<div class="grid-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
}
```
#### Giải thích 
1. `display: grid` cho phép grid.
2. `justify-content: center` đặt phần tử con nằm ở trung tâm theo chiều ngang.
3. `align-items: center` đặt phần tử con nằm ở trung tâm theo chiều dọc.

#### Trình duyệt hỗ trợ
87.6 %

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-grid

### Bố cục Grid
Bố cục website cơ bản sử dụng `grid`

#### HTML

```html
<div class="grid-layout">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">
    Content
    <br>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
  </div>
  <div class="footer">Footer</div>
</div>
```

#### CSS

```css
.grid-layout {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    'sidebar header header'
    'sidebar content content'
    'sidebar footer  footer';
  color: white;
}
.grid-layout > div {
  background: #333;
  padding: 10px;
}
.sidebar {
  grid-area: sidebar;
}
.content {
  grid-area: content;
}
.header {
  grid-area: header;
}
.footer {
  grid-area: footer;
}
```

#### Giải thích 
1. `display: grid` cho phép grid.
2. `grid-gap: 10px` định nghĩa khoảng trắng giữa các phần tử.
3. `grid-template-columns: repeat(3, 1fr)` định nghĩa 3 cột có cùng kích thước.
4. `grid-template-areas` định nghĩa những tên vùng grid.
5. `grid-area: sidebar` khiến phần tử sử dụng khu vực có tên là `sidebar`.

#### Trình duyệt hỗ trợ 
87.6%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-grid

### Loại bỏ text

Nếu text dài hơn một dòng, nó sẽ bị cắt bỏ và kết thúc với dấu chấm lửng `...`

#### HTML

```html
<p class="truncate-text">If I exceed one line's width, I will be truncated.</p>
```

#### CSS

```css
.truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
}
```

#### Giải thích

1. `overflow: hidden` ngăn phần text tràn quá kích thước nó (với block thì 100% width và auto height ).
2. `white-space: nowrap`  ngăn văn bản không vượt quá 1 dòng chiều cao.
3. `text-overflow: ellipsis` làm nó kết thúc với dấu chẩm lửng khi text vượt quá kích thước.
4. `width: 200px;` cho phần tử một kích thước để biết lúc nào lấy dấu chấm lửng.

#### Trình duyệt hỗ trợ 
98.4% 

<span class="snippet__support-note">⚠️ Chỉ hoạt động với các phần từ 1 dòng..</span>

* https://caniuse.com/#feat=text-overflow

### Vòng tròn

Tạo một hình tròn với css thuần.

#### HTML

```html
<div class="circle"></div>
```

#### CSS

```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```

##### Giải thích 

`border-radius: 50%` đường cong viền của phần tử tạo một vòng tròn.

Bời vì vòng tròn có góc bằng nhau tại bất kỳ điểm nào, nên `width` và `height` phải giống nhau. Nếu khác nhau sẽ tạo hình eclipse.

#### Trình duyệt hỗ trợ 
95.5% 

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=border-radius

### Tùy chình thanh cuộn

Tùy chỉnh mẫu thanh cuộn cho tài liệu và các phần tử với scrollable overflow, trên các nền tảng WebKit.

#### HTML

```html
<div class="custom-scrollbar">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
/* Document scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

/* Scrollable element */
.some-element::webkit-scrollbar {
}
```

#### Giải thích

1. `::-webkit-scrollbar` chọn toàn bộ phần tử thanh cuộn.
2. `::-webkit-scrollbar-track` chỉ chọn phần tử scrollbar-track.
3. `::-webkit-scrollbar-thumb` chỉ chọn phần tử scrollbar-thumb.

Có rất nhiều phần tử mẫu khác mà bạn có thể sử dụng để tạo mẫu thanh cuộn. Chi tiết hơn, ghé trang [WebKit Blog](https://webkit.org/blog/363/styling-scrollbars/)

#### Trình duyệt hỗ trợ
88.0%

<span class="snippet__support-note">⚠️ Kiểu thanh cuốn không xuất hiện trên các đường tiêu chuẩn.</span>

* https://caniuse.com/#feat=css-scrollbar

### Tùy chỉnh bộ chọn văn bản 
Thay đổi kiểu của bộ chọn văn bản 
#### HTML

```html
<p class="custom-text-selection">Select some of this text.</p>
```

#### CSS

```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```

#### Giải thích 
`::seclection` định nghĩa một bộ chọn giả trong một phần tử để định kiểu văn bản khi nó được chọn. Chú ý là nếu bạn không phối hợp nhiều bộ chọn kiểu của bạn khác nhau thì nó sẽ được áp dụng chế độ gốc, với bầy kì phần tử có thể chọn nào.

#### Trình duyệt hỗ trợ
84.9%

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để hỗ trợ đầy đủ và không thực sự đúng trong bất kỳ hoàn cảnh nào.</span>

* https://caniuse.com/#feat=css-selection

### Dynamic shadow
Tạo bóng giống như 'box-shadow' nhưng dựa trên màu của chính phần tử.

```html
<div class="dynamic-shadow-parent">
  <div class="dynamic-shadow"></div>
</div>
```

#### CSS

```css
.dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```

#### Giải thích

Phần này yêu cầu 1 tập định nghĩa phức tạp để thực hiện đúng, như là phần tử mẫu sẽ được đặt ngay dưới chính nó trong khi vẫn hiện.

1. `position: relative` ở phần tử cha thiết lập ~~định nghĩa~~ vị trí Cartesian cho các phần tử con.
2. `z-index: 1` thiếp lập 1 lớp định nghĩa mới
3. `position: relative` ở phần tử con thiết lập dịnh nghĩa vị trí cho phần tử mẫu
4. `::after` định nghĩa 1 phần tử mẫu
5. `position: absolute` tách phần tử mẫu ra khỏi luồng tài liệu và đặt nó ở vị trí relation với cha nó.
6. `width: 100%` and `height: 100%` làm kích thước phần tử mẫu lấp đầy kích thước cha nó, làm nó cần bằng về kích thước.
7. `background: inherit` khiến phần tử mẫu thừa kế quy định về góc tuyến tính trên phần tử.
8. `top: 0.5rem` làm nhô phần tử mẫu xuống dưới cha nó.
9. `filter: blur(0.4rem)` sẽ làm mờ phần từ mẫu để tạo bóng phía dưới.
10. `opacity: 0.7` khiến phần tử mẫu trong suốt 1 phần
11. `z-index: -1` đặt phần tử mẫu sau cha của nó

#### Trình duyệt hỗ trợ
91.7%

<span class="snippet__support-note">⚠️ Cần tiền tố để hỗ trợ đầy đủ.</span>

### Khắc văn bản 

Tạo một hiệu ứng văn bản được khắc vào background

#### HTML

```html
<p class="etched-text">I appear etched into the background.</p>
```

#### CSS

```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```

#### Giải thích 
`text-shadow: 0 2px white` tạo một bóng trắng lệch `0px` theo chiều ngang và `2px` theo chiều dọc từ vị trí ban đầu.

Background phải đậm hơn bóng của hiệu ứng để hoạt động.

Màu của văn bản nên được làm mờ nhạt để nó nhìn giống như khắc vào background.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Không .</span>

* https://caniuse.com/#feat=css-textshadow

<!-- tags: visual -->
### Văn bản Gradient

cho văn bản một màu gradient

#### HTML

```html
<p class="gradient-text">Gradient text</p>
```

#### CSS

```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```


#### Giải thích

1. `background: -webkit-linear-gradient(...)` cho phần tử text màu gradient.
2. `webkit-text-fill-color: transparent` đổ vào đoạn text màu gradient.
3. `webkit-background-clip: text` clip nền với văn bản, điền vào các văn bản với nền gradient như màu sắc.

#### Trình duyệt hỗ trợ 

<span class="snippet__support-note">⚠️ Uses non-standard properties.</span>

* https://caniuse.com/#feat=text-stroke

<!-- tags: visual -->

### Viền mảnh

Cho phần tử 1 đường viền tương đương 1 pixel thiết bị tự nhiên chiều rông, nhìn trống rất nhọn và sắc nét

#### HTML

```html
<div class="hairline-border">text</div>
```

#### CSS

```css
.hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
```

#### Giải thích

1. `box-shadow`, chỉ khi sử dụng rộng rãi, thêm các viền mẫu có thể sử dụng subpixels\*
2. Sử dụng `@media (min-resolution: ...)` để kiểm tra tỉ lệ pixel của thiết bị (`1dppx` tương đương 96 DPI),
  cài đặt rộng rãi `box-shadow` tương đương `1 / dppx`.

#### Trình duyệt hỗ trợ
95.5%

<span class="snippet__support-note">⚠️ Cần cú pháp so le và kiểm tra user agent để hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=css-boxshadow
* https://caniuse.com/#feat=css-media-resolution

<hr>

\*Chrome không hỗ trợ subpixel value trong `border` . Safari không hỗ trợ subpixel value trong `box-shadow`. Firefox hỗ trợ subpixel values trong cả hai.

<!-- tags: visual -->

### :not selector

Bộ chọn giả `:not` sử dụng cho việc tạo kiểu của một nhóm phẩn tử, trong đó không áp dụng cho phẩn tử cuối (hoặc xác định rõ)
#### HTML
```html
<ul class="css-not-selector-shortcut">
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
  <li>Four</li>
  <li>Five</li>
</ul>
```
#### CSS
```css
.css-not-selector-shortcut {
  display: flex;
}
li {
  list-style-type: none;
  margin: 0;
  padding: 0 0.75rem;
}
li:not(:last-child) {
  border-right: 2px solid #d2d5e4;
}
```
#### Giải thích
`li:not(:last-child)` quy định rằng kiểu áp dụng cho toàn bộ phần tử `li` trừ `:last-child`

### Cuộn tràn

Thêm 1 cái dốc mờ vào phần từ tràn để biểu thị rõ hơn việc có thêm nội dung có thể cuộn.

#### HTML

```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Content to be scrolled
  </div>
</div>
```

#### CSS

```css
.overflow-scroll-gradient {
  position: relative;
}
.overflow-scroll-gradient::after {
  content: '';
  position: absolute;
  bottom: 0;
  width: 240px;
  height: 25px;
  background: linear-gradient(
    rgba(255, 255, 255, 0.001),
    white
  ); /* transparent keyword is broken in Safari */
  pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
```


#### Giải thích

1. `position: relative` trên phần tử cha thiết lập 1 định nghĩa vị trí Cartesian cho phần tử mẫu. 
2. `::after` định nghĩa 1 phần tử mẫu
3. `background-image: linear-gradient(...)` thêm 1 dốc tuyến tính mờ dần từ trong suốt trên trắng (trên xuống dưới)
4. `position: absolute` đấy phần tử mẫu ra khỏi luồng tài liệu và đặt vị trí nó relation với cha nó.
5. `width: 240px` gán kích thước của phần tử cuộn ( con của cha có phần tử mẫu)
6. `height: 25px` là chiều cao của phần tử mẫu mờ dốc, nên giữ nhỏ tương đối
7. `bottom: 0` đặt vị trí phần tử mẫu dưới cùng của ch
8. `pointer-events: none` quy định phần tử mẫu không thể bị chọn với sự kiện chuột, cho phép chữ đắng sau vẫn có thể được chọn/ tương tác

#### Trình duyệt hỗ trợ 
95.4%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->

### Gạch dưới chữu đẹp hơn

1 thay thế đẹp hơn của `text-decoration: underline` khi phần hạ xuống không ghim gạch dưới.
Thực hiện tự nhiên `text-decoration-skip-ink: auto` nhưng khó kiểm soát gạch dưới hơn

#### HTML

```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```

#### CSS

```css
.pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px;
  text-shadow: 1px 1px 0 #f5f6f9, -1px 1px 0 #f5f6f9, -1px -1px 0 #f5f6f9, 1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}
.pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
.pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
```



#### Giải thích

1. `text-shadow: ...` có 4 giá trị bù bao quanh 1 vùng 4x4 px để đảm bảo đường gạch dưới có 1 bóng mỏng bao cái đường mà phần hạ xuống ghim vào
Sử dụng mãu sắc phù hợp với nền. Với font lớn hơn, sử dụng kích thướng `px` lớn hơn.
2. `background-image: linear-gradient(...)` tạo 1 dốc 90 độ với màu chữ hiện tại(`currentColor`)
3.  `background-*` định nghĩa kích thước dốc bằng 1x1px ở cuối và lặp lại suốt x-
4. bộ chọn mẫu `::selection` đảm bảo bóng chữ không cẩn trở khi chọn ch

#### Trình duyệt hỗ trợ
95.4%

<span class="snippet__support-note">⚠️ Khoảng cách của gạch dưới tới chữ phụ thuộc vào chuẩn đo của font,do vậy bạn phải đảm bảo rằng mọi người đều thấy cùng 1 font (i.e. không có font thấy đổi trên nền OS).</span>

* https://caniuse.com/#feat=css-textshadow
* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->

### Đặt lại toàn bộ kiểu

Đặt lại toàn bộ kiểu về giá trị mặc định với 1 thuộc tính. Nó sẽ không ảnh hưởng tới thuộc tính `direction` và `unicode-bidi`

#### HTML

```html
<div class="reset-all-styles">
  <h4>Title</h4>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
.reset-all-styles {
  all: initial;
}
```


#### Giải thích

Thuộc tính `all` cho phép bạn đặt lại toàn bộ kiểu(cả thừa hưởng hay không) về mặc định

#### Trình duyệt hỗ trợ
98.3%

<span class="snippet__support-note">⚠️ MS Edge trạng thái đang cđược ân nhắc.</span>

* https://caniuse.com/#feat=css-all

<!-- tags: visual -->

### Bộ tách khối

Sử dụng khối SVG để tách 2 khối khác nhau để tạo thêm các hình trực quan thú vị so với bộ tách ngang tiêu chuẩn

#### HTML

```html
<div class="shape-separator"></div>
```

#### CSS

```css
.shape-separator {
  position: relative;
  height: 48px;
  background: #333;
}
.shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
```


#### Giải thích

1. `position: relative`trên phần tử thiết lập 1 định  nghĩa vị trí Cartesian cho phần tử mẫu
2. `::after` định nghĩa 1 phàn tử mẫu
3. `background-image: url(...)` thêm 1 khối SVG (1 tam giác 24x24 trên định dạng base64) như là ảnh nền của phần tử mẫu, mặc định tự lặp
Nó phải cùng màu với khối được chia
4. `position: absolute` mang phần tử mẫu ra khỏi tài liệu và đặt nó ở vị trí relation với cha nó
5. `width: 100%` đảm bảo phần tử trải dài chiều rộng cha nó
6. `height: 24px` là chiều cao tương tự như khối.
7. `bottom: 0` đặt phần tử mẫu ở cuối cha nó

#### Trình duyệt hỗ trợ
98.3%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=svg

<!-- tags: visual -->

### Tập font hệ thống

Sử dụng font tự nhiên hệ thống để có cảm giác ứng dụng tự nhiên gần gũi hơn

#### HTML

```html
<p class="system-font-stack">This text uses the system font.</p>
```

#### CSS

```css
.system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```


#### Giải thích

Trình duyệt tìm kiếm mỗi font kế tiếp, ưu tiên cái đầu tiên có thể, và đến tiếp cái tiếp theo nếu không thể tìm thấy font(trên hệ thống hoặc định nghĩa trong css)

1. `-apple-system` là San Francisco, sử dụng trên iOs và macOs(tuy nhiên không phải Chrome)
2. `BlinkMacSystemFont` là San francisco, sử dụng trên macOs chrome
3. `Segoe UI` sử dụng trên Windows 10
4. `Roboto` sử dụng trên Android
5. `Oxygen-Sans` sử dụng trên GNU+Linux
6. `Ubuntu` sử dụng trên Linux
7. `"Helvetica Neue"` vaf `Helvetica` sử dụng trên macOS 10.10 và thấp hơn (gói trong trích dẫn vì nó có khoảng trống)
8. `Arial` là font được sử dụng rỗng rãi bởi tất cả hệ điều hành
9. `sans-serif` là font sans-serif  dự phòng khi không cái nào khác hộ tr

#### Trình duyệt hỗ trợ
99+%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

<!-- tags: visual -->

### Tam giác

Tạo 1 hình tam giác với CSS thuần
#### HTML

```html
<div class="triangle"></div>
```

#### CSS

```css
.triangle {
  width: 0;
  height: 0;
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```



#### Giải thích

[Xem link này để giải thích chi tiết.](https://stackoverflow.com/q/7073484)

Màu sắc của viền là màu của tam giác. Cạnh của các đỉnh tam giác tương ứng đối xứng với thuộc tính `border-*`. Ví dụ màu của `border-top` nghĩa
điểm nhọn bên dưới

Thí nghiệm với giá trị `px` để thay đổi tỉ lệ tam giác

#### Trình duyệt hỗ trợ
99+%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

<!-- tags: visual -->

### Tải nảy lên

Tạo hiệu ứng tải nảy lên

#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```



#### Giải thích

Ghi chú: `1rem` thường là `16px`.

1. `@keyframes` định nghĩa 1 hiệu wungs với 2 trạng thái, khi phần tử thay đổi `opacity` và chuyển dạng 2D sử dụng `transform: translateY()`

2. `.bouncing-loader` là khung chứa cha của vòng nảy và sử dụng `display: flex`
   và `justify-content: center` để đặt nó ở g

3. `.bouncing-loader > div`, chọn 3 phần tử `div`s của cha để tạo kiểu. `div`s được gán chiều cao và chiều rộng `1rem`, sử dụng `border-radius: 50%` để chuyển từ hình vuông thành tròn

4. `margin: 3rem 0.2rem` quy định mỗi hình tròn có top/bottom margin là `3rem` và left/right margin
   là `0.2rem` để nó không chạm vào nhau, cho nó 1 ít khoảng trống

5. `animation` là thuộc tính viết tắt của nhiều thuộc tính hiệu ứng: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction` được sử dụng.

6. `nth-child(n)` chọn phần tử con thứ n của cha nó

7. `animation-delay` được sử dụng lần lượt trên phàn tử `div` thứ 2 và 3 , để nó không bắt đầu hiệu ứng cùng lúc

#### Trình duyệt hỗ trợ
95.3%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->

### Con quay Donut 

Tạo con quay donut để biểu thị tải nội dung

#### HTML

```html
<div class="donut"></div>
```

#### CSS

```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```



#### Giải thích

Sử dụng semi-transparent `border`cho toàn bộ phần tử, trừ cái làm con chỉ thị tải của donut. Sử dụng `animation` để xoay phần tử

#### Trình duyệt hỗ trợ
95.3%

<span class="snippet__support-note">⚠️ Cần tiền tố để hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=css-animation
* https://caniuse.com/#feat=transforms2d

<!-- tags: animation -->

### Easing variables

Các biển đểu có thể sử dụng lại cho thuộc tính`transition-timing-function`. mạnh mẽ hơn các built-in `ease`, `ease-in`, `ease-out` và `ease-in-out`.

#### HTML

```html
<div class="easing-variables"></div>
```

#### CSS

```css
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.easing-variables {
  width: 50px;
  height: 50px;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}

.easing-variables:hover {
  transform: rotate(45deg);
}
```



#### Giải thích

Các biến được định nghĩa toàn cục trong lớp mẫu CSS `:root` ứng với phần tử gốc của cây đại diện cho tài liệu. Trong HTML, `:root` đại diện cho phần tử `<html>` và giống với bộ chọn `html`, trừ khi đặc tính của nó cao hơn

#### Trình duyệt hỗ trợ
88.0%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: animation -->

### Hiệu ứng hover kẻ chân

Tạo hiệu ứng kẻ chân khi chữ được hover

<small>**Credit:** https://flatuicolors.com/</small>

#### HTML

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

#### CSS

```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```


#### Giải thích

1. `display: inline-block` khiến khối `p` và `inline-block` tránh kẻ chân từ việc kéo dài chiều dài cha nó hơn nội dung(chữ)
2. `position: relative` trên phần tử thiết lập định nghĩa vị trí Cartesian cho phần tử mẫu
3. `::after` định nghĩa phần tử mẫu
4. `position: absolute` mang phần tử mẫu ra khỏi luồng tài liệu và đặt nó relation với cha nó
5. `width: 100%` đảm bảo phần tử mẫu trải dài toàn bộ chiều rộng của khối chữ
6. `transform: scaleX(0)` khởi tạo scale cho phần từ mẫu về 0 để nó không có chiều rộng và không hiện
7. `bottom: 0` và `left: 0` đặt nó ở góc dưới trái của khối
8. `transition: transform 0.25s ease-out` nghĩa là thay đổi `transform` sẽ được chuyển trong 0.25 giấy với hàm tính giờ `ease-out`.
9. `transform-origin: bottom right` nghĩa là thay đổi điểm neo là đặt tại góc dưới bên phải khối
10. `:hover::after` sau đó dùng `scaleX(1)` để chuyển đổi chiều rộng thành 100%, sau đó thay đổi `transform-origin`
    thành `bottom left` để điểm neo ngược lại, cho phép nó chuyển đổi sang hướng khác khi hover ra

#### Trình duyệt hỗ trợ
95.4%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=transforms2d
* https://caniuse.com/#feat=css-transitions

<!-- tags: animation -->

### Tắt chọn

Khiến nội dung không chọn dược

#### HTML

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

#### CSS

```css
.unselectable {
  user-select: none;
}
```


#### Giải thích

`user-select: none` đặc tả nội dung không thể bị chọn

#### Trình duyệt hỗ trợ
95.3%

<span class="snippet__support-note">⚠️ Cần tiền tố để hỗ trợ đầy đủ.</span>
<span class="snippet__support-note">⚠️ This is not a secure method to prevent users from copying content.</span>

* https://caniuse.com/#feat=user-select-none

<!-- tags: interactivity -->

### Theo dõi dốc con chỏ chuột

Hiệu ứng hover khi dốc theo con trỏ chuột

<small class="snippet__credit">**Credit:** [Tobias Reich](https://codepen.io/electerious/pen/MQrRxX)</small>

#### HTML

```html
<button class="mouse-cursor-gradient-tracking">
  <span>Hover me</span>
</button>
```

#### CSS

```css
.mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.mouse-cursor-gradient-tracking span {
  position: relative;
}

.mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, pink, transparent);
  transform: translate(-50%, -50%);
  transition: width 0.2s ease, height 0.2s ease;
}

.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

#### JavaScript

```js
var btn = document.querySelector('.mouse-cursor-gradient-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```


#### Giải thích

_TODO_

**Ghi chú!**

Nếu cha phần tử có định  nghĩa vị trí (`position: relative`), bạn sẽ cần khử phần bù của nó nữa

```js
var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
```

#### Trình duyệt hỗ trợ
88%

<div class="snippet__requires-javascript">Yêu cầu JavaScript</div>
<span class="snippet__support-note">⚠️ Yêu cầu JavaScript.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: visual, interactivity -->

### Menu bật ra

Xuất hiện 1 menu tương tác bật ra khi hover.

#### HTML

```html
<div class="reference">
  <div class="popout-menu">
    Popout menu
  </div>
</div>
```

#### CSS

```css
.reference {
  position: relative;
}
.popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
}
.reference:hover > .popout-menu {
  visibility: visible;
}
```


#### Giải thích

1. `position: relative` ở phần tử cha liên quan thiết lập định nghĩa vị trí cho con nó
2. `position: absolute` mang menu bật ra khỏi luồng tài liệu và đặt nó relation với cha nó
3. `left: 100%` chuyển menu về phía trái 100% của cha nó
4. `visibility: hidden` khởi tạo ẩn menu và cho phép chuyển đổi (không giống `display: none`)
5. `.reference:hover > .popout-menu` nghĩa là khi `.reference` được hover, chọn ngay lập tức con với class
  `.popout-menu` và thay đổi `visibility` của chúng thành `visible`, sẽ hiện cái menu bật ra.

#### Trình duyệt hỗ trợ
99+%
<span class="snippet__support-note">✅ Không có cảnh báo.</span>

<!-- tags: interactivity -->

### Mờ sibling

Làm mở siblings của mục được hover

#### HTML

```html
<div class="sibling-fade">
  <span>Item 1</span>
  <span>Item 2</span>
  <span>Item 3</span>
  <span>Item 4</span>
  <span>Item 5</span>
  <span>Item 6</span>
</div>
```

#### CSS

```css
span {
  padding: 0 1rem;
  transition: opacity 0.2s;
}

.sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
```



#### Giải thích

1. `transition: opacity 0.2s` đặc tả thay đổi của opacity sẽ chuyển đổi trong 0.2 giây
2. `.sibling-fade:hover span:not(:hover)` đặc tả khi cha được hover, chọn bất kỳ con `sqan` không hđược over và đổi opacity của chúng về `0.5`

#### Trình duyệt hỗ trợ
99+%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-sel3
* https://caniuse.com/#feat=css-transitions

<!-- tags: interactivity -->

### Tùy biến biến

Các biến CSS chưa các giá trị đặc tả có thể sử dụng xuyên suốt tài liệu

#### HTML

```html
<p class="custom-variables">CSS is awesome!</p>
```

#### CSS

```css
:root {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
}

.custom-variables {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```

#### Giải thích

Các biến được định nghĩa toàn cục trong class gốc CSS `:root` ứng với phần tử gốc của cây đại diên tài liệu. Các biến cũng có thể mở rộng thành 1 bộ chón nếu được định nghĩa trong khối

Định nghĩa biến với `--variable-name:`.

Sử dụng lại biến xuyển suốt tài liệu sử dụng hàm `var(--variable-name)` .

#### Trình duyệt hỗ trợ
87.2%

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: other -->
