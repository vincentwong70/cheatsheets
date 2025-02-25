# Go Cheat Sheet

## Data Types

### Strings

```go
    var myString string = 'Hello World'
    var myString string = `Hello World`
    myString string := 'Hello' + ' ' + 'World'
```

```go
     var myString string = 'Hello World'
     len(myString) -> will give number of bytes used by the string

     utf8.RuneCountInString(myString) -> will give the length
```

### Numbers

#### Types

```go
- int, int8 int16, int32, uint, uint8, uint16, uint32

- float32, float64

- var1, var2 := 1, 2
```

#### Operations

```go
# Divison will round down by default
fmt.Println(3 / 2) -> 1

# cannot do operation between integers and floats
fmt.Println(float + int)
```

### Boolean

```go
    var myBoolean bool = true

    const myBoolean bool = false
```

## Functions

```go
    import (
        "errors"
        "fmt"
    )

    func main() {
        const printValue string = "Hello World"

        const numerator int = 11
        const denominator int = 2
        const result, remainder, err = intDivision(numerator, denominator)

        if err != nil {
            fmt.Printf(err.Error())
        } else if reminaer == 0 {
            fmt.Printf("...)
        } else {
            fmt.Printf("..")
        }

        fmt.Printf("The result of the integer is %v with remainder %v", result, remainder)
    }

    funct printMe(printValue string) {
        fmt.Println(printValue)
    }

    func intDivision(numerator int, denominator int) (int, int, error) {
        var err error

        if denominator == 0 {
            err = errors.New("Cannot Divide by Zero")
            return 0, 0, err
        }

        result := numerator / denominator
        remainder := numerator % denominator
        return result, remainer, err
    }
```

## Control Flow

```go
if val == val || val != val && val == val {
 ...
} else if (boolean) {
    ..
} else {
    ...
}

switch {
    boolean:
        logic
    default:
        logic
}

switch value {
    0:
        logic
    1:
        logic
}
```

## Arrays, Slice, Maps, Loops

```go
import "fmt"

package main

func main() {
    # define an array
    var intArr [3]int32 = []int32{4,5,6}

    # index/slice an array
    fmt.Println(intArr[0])
    fmt.Println(intArr[1:3])

    # add to an array
    intSlice = append(intSlice, 7)

    # maps

    var myMap map[string]uint8 = make(map[string]uint8)
    var myMap2 = map[string]uint8 { "Adam": 23, "Sarah": 45 }

    myMap2["Jason"] --> 0 returns default value of type of not exist

    // value, if value is in the map
    var age, ok = myMap2["Jason"]

    // delete from map
    delete(myMap2, "Adam")

    // iterate
    for name, age := range myMap2 {
        fmt.Printf("Name: %v\n", name)
    }

    for index, value := range intArr {
        // logic
    }

    for i := 0; i < 10; i++ {
        fmt.Println(i)
    }
}

```

## Structs

```go

type gasEngine struct {
    mpg uint8
    gallons uint8
    owner
}

# Assign method to gasEngine struct
func (e gasEngine) milesLeft() uint8 {
    return e.gallons * e.mpg
}

type owner struct {
    name string
}

func main() {
    const myEngine gasEngine = gasEngine{ mpg: 25, gallons: 15 }
    myEngine.mpg = 20

    # Anonymous struct
    const myEngine2 struct {
        mpg uint8
        gallons uint8
    }{25, 15}

    # call method
    myEngine.milesLeft()
}

```

## Pointers

```go
func main() {
    var p *int32 = new (int32)
    var i int32

    *p = &i
}
```

## Goroutines

Allows us to run functions concurrently and wait for them to finish via a wait group which is essentially a counter.

Use a mutex to prevent multiple goroutines from modifying the same resource at a single time

```go
import (
    "fmt",
    "time",
    "sync"
)

var m =sync.Mutex{}
var wg = sync.WaitGroup{}
var dbData = []string{"id1", "id2", "id3", "id4", "id5"}
var results = []string{}

func main() {
    t0 := time.Now()

    for i:=0; i < len(dbData); i++ {
        wg.Add(1)
        go dbCall(i)
    }

    wg.Wait()
    fmt.Printf("Total executiontime: %v", time.Since(t0))
}

func dbCall(i int) {
    var delay float32 = 2000
    time.Sleep(time.Duration(delay) * time.Millisecond)
    fmt.Println("The result from the database is: %v", dbData[i])

    m.Lock()
    results = append(results, dbData[i])
    m.Unlock()
    wg.Done()
}

```

## Channels

Channels are a way to send and receive blocks and data and are typically used with Goroutines.

```go
package main

import "fmt"

func sum(s []int, c chan int) {
	sum := 0
	for _, v := range s {
		sum += v
	}
	c <- sum // send sum to c
}

func main() {
	s := []int{7, 2, 8, -9, 4, 0}

	c := make(chan int)
	go sum(s[:len(s)/2], c)
	go sum(s[len(s)/2:], c)
	x, y := <-c, <-c // receive from c, wait for channels to be set by goroutines

	fmt.Println(x, y, x+y)
}
```

## Generics

Define a generic parameter into a function or struct

```go
type gasEngine struct {
gallons float32
mpg float32
}

type electricEngine struct {
kwh float32
mpkwh float32
}

type car[T gasEngine | electricEngine] struct {
carMake string
carModel string
engine T
}

```
