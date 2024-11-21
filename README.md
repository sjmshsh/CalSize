# CalSize
Go计算大小


```go
package main

import (
	"fmt"

	// Use latest tag.
	"github.com/DmitriyVTitov/size"
)

func main() {
	a := struct {
		a int
		b string
		c bool
		d int32
		e []byte
		f [3]int64
	}{
		a: 10,                    // 8 bytes
		b: "Text",                // 16 (string itself) + 4 = 20 bytes
		c: true,                  // 1 byte
		d: 25,                    // 4 bytes
		e: []byte{'c', 'd', 'e'}, // 24 (slice itself) + 3 = 27 bytes
		f: [3]int64{1, 2, 3},     // 3 * 8 = 24 bytes
	} // 84 + 3 (padding) = 87 bytes

	fmt.Println(size.Of(a))
}

// Output: 87
```