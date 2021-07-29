---
layout: post
title:  "Go Lang Keep Book "
date:   2021-07-21
categories: GoLang
tag: Golang
---
### WHAT IS GOLAND?

Golang là một ngôn ngữ mạnh về ```concurrent programs```

1. Các cách khai báo biến
{% highlight golang %}
var a int
var b = 0
var c, d int
var e, f = 0 , 1
var x := 2.3
var (
    name = "Golang"
    version = 16.1
)
{% endhighlight %}

với toán tử ```:=``` chị được dùng trong khai báo lần đầu và phải được gián với giá trị khởi tạo trong

Go là một ngôn ngữ định kiểu, có nghĩa là không thể thay đổi kiểu cho biến đã xác định type

Convention for biến:
* A name must begin with a letter , and can have any number of additional letters and numbers.
* A variable name can't start with a number
* A name can't contain space
* If the name of a variable begins with a lower-case letter, it can only accessed with the current package this is considered as ```unexported``` variables
* If the name of a variable begins with a capital letter, it can be accessed from  packages outside the current package one this is considered as ```exported``` variables
* If a name consists of multiple word, each word after the first should be capitalized like this: empName, EmpAddress, etc.
* Variable names are case-sensitive (car, Car and CAR are three different variables)

2. Hằng số (CONSTANTS)

Hằng số được khai báo với keyword ```const```

Convention for constants:
* Name of constants must follow the same rules as variable names, which means a valid constants name must starts with a letter or underscore.
* By convention, constant names are  usually written in uppercase letters. This is for their easy indentification and  differentiation and differentiation from variables in the source code.

3. Kiểu dữ liệu (Data Type)

GoLang is statically typed programing language.
Type Convert:
```string``` to ```int``` ==> strconv.Atoi(str)
```string``` to ```float``` ===> strconv.ParseFloat(s string, bitSize int) bigSize = {32: float32, 64: float64}
```string``` to ```boolean``` ==> strconv.ParseBool(s string). Accepted values = [ 1, t, T, TRUE, true, True, 0, f, F, FALSE, false, False]
```boolean``` to ```string``` ==> strcnv.FormatBool(bool)
```float``` to ```string``` ==> strcnv.FormatFloat(f float64, fmt byte, prec, bigSize int) fmt: according to the format, prec = precision( độ chính xác)
{% highlight golang %}
	var s string = strconv.FormatFloat(f, 'E', -1, 32)
{% endhighlight %}
```int``` to ```string``` ==> strcnv.FormatInt(i int, base int) base = hệ số 
```int``` to ```float``` ==> int32(f) , float32(i), int64(f), float64(i)

4. If ... Else Conditional

{% highlight golang %}
if  condition { 
    // code to be executed if condition is true
}

if  condition { 
    // code to be executed if condition is true
} else {
    // code to be executed if condition is false
}

if  condition-1 { 
    // code to be executed if condition-1 is true
} else if condition-2 {
    // code to be executed if condition-2 is true
} else {
    // code to be executed if both condition1 and condition2 are false
}

if  var declaration;  condition { 
    // code to be executed if condition is true
}

package main
 
import (
	"fmt"
)
 
func main() {
	if x := 100; x == 100 {
		fmt.Println("Germany")
	}
}

{% endhighlight %}

5. Switch case Conditional

{% highlight golang %}
today := time.Now()
switch today.Day() {
case 5:
    fmt.Println("Today is 5th. Clean your house.")
case 10:
    fmt.Println("Today is 10th. Buy some wine.")
case 15:
    fmt.Println("Today is 15th. Visit a doctor.")
case 25:
    fmt.Println("Today is 25th. Buy some food.")
case 31:
    fmt.Println("Party tonight.")
default:
    fmt.Println("No information available for that day.")
}

today := time.Now()
var t int = today.Day()

switch t {
case 5, 10, 15:
    fmt.Println("Clean your house.")
case 25, 26, 27:
    fmt.Println("Buy some food.")
case 31:
    fmt.Println("Party tonight.")
default:
    fmt.Println("No information available for that day.")
}

{% endhighlight %}

```fallthroungh``` dùng để pass block tiếp theo của case.

6. For Loop

{% highlight golang %}
k := 1
for ; k <= 10; k++ {
    fmt.Println(k)
}

k = 1
for k <= 10 {
    fmt.Println(k)
    k++
}

for k := 1; ; k++ {
    fmt.Println(k)
    if k == 10 {
        break
    }
}

"
// Example 1
strDict := map[string]string{"Japan": "Tokyo", "China": "Beijing", "Canada": "Ottawa"}
for index, element := range strDict {
    fmt.Println("Index :", index, " Element :", element)
}

// Example 2
for key := range strDict {
    fmt.Println(key)
}

// Example 3
for _, value := range strDict {
    fmt.Println(value)
}


// Range for "string"
for range "Hello" {
    fmt.Println("Hello")
}

//Infinite loop
for {
    fmt.Println("Hello")
    if i == 10 {
        break
    }
    i++
}
{% endhighlight%}

7. Functions

Function được khai báo bằng keyword ```func```

If the functions with names that start with an uppercase letter will be exported to other packages. If the function name starts with a lowercase letter, it won't be exported to other packages, but you can call this function within the same package.

Function của go có option ràng buộc giá trị trả về

{% highlight golang %}
function
// Function with int as return type
func add(x int, y int) int {
	total := 0
	total = x + y
	return total
}
{% endhighligen %}

Có thể đặt tên cho giá trị trả về của function
{% highlight golang %}
func rectangle(l int, b int) (area int) {
	var parameter int
	parameter = 2 * (l + b)
	fmt.Println("Parameter: ", parameter)

	area = l * b
	return // Return statement without specify variable name
}

func rectangle(l int, b int) (area int, parameter int) {
	parameter = 2 * (l + b)
	area = l * b
	return // Return statement without specify variable name
}
{% endhighligen %}

Convention for named function:
* A name must begin with a letter, and can have any number of additional letters and numbers.
* A function name cannot start with a number.
* A function name cannot contain spaces.
* If the functions with names that start with an uppercase letter will be exported to other packages. If the function name starts with a lowercase letter, it won't be exported to other packages, but you can call this function within the same package.
* If a name consists of multiple words, each word after the first should be capitalized like this: empName, EmpAddress, etc.
* function names are case-sensitive (car, Car and CAR are three different variables).

Nếu chữ cái đầu viết hoa ~= ```static```

Có thể pass địa chỉ con trỏ là argument như trong C.
{% highlight golang %}
package main

import "fmt"

func update(a *int, t *string) {
	*a = *a + 5      // defrencing pointer address
	*t = *t + " Doe" // defrencing pointer address
	return
}

func main() {
	var age = 20
	var text = "John"
	fmt.Println("Before:", text, age)

	update(&age, &text)

	fmt.Println("After :", text, age)
}
{% endhighligen %}

Anonymous function

Có thể chỉ định một funcion cho một biến mà không cần khai báo tên func
{% highlight golang %}
package main

import "fmt"

var (
	area = func(l int, b int) int {
		return l * b
	}
)

func main() {
	fmt.Println(area(20, 30))
}
{% endhighligen %}

{% highlight golang %}
package main

import "fmt"

func main() {
	func(l int, b int) {
		fmt.Println(l * b)
	}(20, 30)
}
{% endhighligen %}

{% highlight golang %}
package main

import "fmt"

func main() {
	fmt.Printf(
		"100 (°F) = %.2f (°C)\n",
		func(f float64) float64 {
			return (f - 32.0) * (5.0 / 9.0)
		}(100),
	)
}
{% endhighligen %}

Closures func là một dạng đặc biệt của Anonymous func nó có thể get biến ngoài body func
{% highlight golang %}
package main

import "fmt"

func main() {
	l := 20
	b := 30

	func() {
		var area int
		area = l * b
		fmt.Println(area)
	}()
}
{% endhighligen %}

{% highlight golang %}
package main

import "fmt"

func main() {
	for i := 10.0; i < 100; i += 10.0 {
		rad := func() float64 {
			return i * 39.370
		}()
		fmt.Printf("%.2f Meter = %.2f Inch\n", i, rad)
	}
}
{% endhighligen %}


Higher Order func là trường hợp một func có thể lấy một func khác làm agrument hay là giá trị trả về

{% highlight golang %}
package main

import "fmt"

func sum(x, y int) int {
	return x + y
}
func partialSum(x int) func(int) int {
	return func(y int) int {
		return sum(x, y)
	}
}
func main() {
	partial := partialSum(3)
	fmt.Println(partial(7))
}
{% endhighligen %}

{% highlight golang %}
package main

import "fmt"

func squareSum(x int) func(int) func(int) int {
	return func(y int) func(int) int {
		return func(z int) int {
			return x*x + y*y + z*z
		}
	}
}
func main() {
	// 5*5 + 6*6 + 7*7
	fmt.Println(squareSum(5)(6)(7))
}

{% endhighligen %}

User Defined Function Types in Golang

Có thể khai báo hàm trước như C
{% highlight golang %}
package main

import "fmt"

type First func(int) int
type Second func(int) First

func squareSum(x int) Second {
	return func(y int) First {
		return func(z int) int {
			return x*x + y*y + z*z
		}
	}
}

func main() {
	// 5*5 + 6*6 + 7*7
	fmt.Println(squareSum(5)(6)(7))
}
{% endhighligen %}



8. Variadic Functions

{% highlight golang %}
package main

import (
	"fmt"
	"reflect"
)
func main() {
	variadicFunc(1, 1.2, "string", []string{"a","b","c"}, true, map[string]int{"apple": 23, "tomato": 13})	
}

func variadicFunc(i ...interface{}){
	for _, v:= range i {
		fmt.Println(v,"--",reflect.ValueOf(v).Kind())
	}
}
{% endhighligen %}

9. Deferred Functions Calls
Go có một câu lệnh đặc biệt gọi là defer lên lịch chạy một lệnh gọi hàm sau khi hàm hoàn thành. Hãy xem xét ví dụ sau:

Tạm hoãn invoke func. Defer Function sẽ được gọi ngay sau khi func chạy xong.

{% highlight golang %}
package main
import "fmt"
func first() {
	fmt.Println("First")
}
func second() {
	fmt.Println("Second")
}
func main() {
	defer second()
	first()
}

{% endhighligen %}


{% highlight golang %}
{% endhighligen %}
{% highlight golang %}
{% endhighligen %}
