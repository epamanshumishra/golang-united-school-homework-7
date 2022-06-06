package coverage

import (
	"os"
	"testing"
	"time"

    "github.com/stretchr/testify/assert"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func TestLen(t *testing.T){
	var p People
	p = append(p, Person{firstName: "Peter", lastName: "Parker", birthDay: time.Now() })
	p = append(p, Person{firstName: "Tony", lastName: "Stark", birthDay: time.Now().Add(time.Minute * 10) })
	p = append(p, Person{firstName: "Clark", lastName: "Kent", birthDay: time.Now().Add(time.Minute * 20) })

    got := p.Len()
    want := 3

    if got != want {
        t.Errorf("got %q, wanted %q", got, want)
    }
}

func TestLessBirthdayFalse(t *testing.T){
	var p People
	p = append(p, Person{firstName: "Peter", lastName: "Parker", birthDay: time.Now() })
	p = append(p, Person{firstName: "Tony", lastName: "Stark", birthDay: time.Now().Add(time.Minute * 10) })

    got := p.Less(0,1)
    want := false

    if got != want {
        t.Errorf("got %v, wanted %v", got, want)
    }
}

func TestLessBirthdayTrue(t *testing.T){
	var p People
	p = append(p, Person{firstName: "Peter", lastName: "Parker", birthDay: time.Now() })
	p = append(p, Person{firstName: "Tony", lastName: "Stark", birthDay: time.Now().Add(time.Minute * 10) })

    got := p.Less(1,0)
    want := true

    if got != want {
        t.Errorf("got %v, wanted %v", got, want)
    }
}

func TestLessFirstNameTrue(t *testing.T){
	var p People
	p = append(p, Person{firstName: "Peter", lastName: "Parker", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })
	p = append(p, Person{firstName: "Tony", lastName: "Stark", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })

    got := p.Less(0,1)
    want := true

    if got != want {
        t.Errorf("got %v, wanted %v", got, want)
    }
}

func TestLessFirstNameFalse(t *testing.T){
	var p People
	p = append(p, Person{firstName: "Peter", lastName: "Parker", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })
	p = append(p, Person{firstName: "Tony", lastName: "Stark", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })

    got := p.Less(1,0)
    want := false

    if got != want {
        t.Errorf("got %v, wanted %v", got, want)
    }
}

func TestLessLastNameFalse(t *testing.T){
	var p People
	p = append(p, Person{firstName: "David", lastName: "Silva", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })
	p = append(p, Person{firstName: "David", lastName: "Miller", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })

    got := p.Less(0,1)
    want := false

    if got != want {
        t.Errorf("got %v, wanted %v", got, want)
    }
}

func TestLessLastNameTrue(t *testing.T){
	var p People
	p = append(p, Person{firstName: "David", lastName: "Silva", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })
	p = append(p, Person{firstName: "David", lastName: "Miller", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })

    got := p.Less(1,0)
    want := true

    if got != want {
        t.Errorf("got %v, wanted %v", got, want)
    }
}

func TestSwap(t *testing.T){
	var p People
	p = append(p, Person{firstName: "David", lastName: "Silva", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })
	p = append(p, Person{firstName: "David", lastName: "Miller", birthDay: time.Date(2009, 11, 17, 20, 34, 58, 651387237, time.UTC) })

	p0 := p[0]
	p1 := p[1]

    p.Swap(1,0)

    if p0 != p[1] || p1 != p[0] {
        t.Errorf("Swap not successful")
    }
}

func TestNewMatrix(t *testing.T) {
    matrixString := `1 2 3
    4 5 6
    7 8 9`

    _, err := New(matrixString)

    if (err != nil) {
        t.Error(err)
    }
}

func TestImproperMatrix(t *testing.T) {
    matrixString := `1 2 3
    4 5 
    7 8 9`

    _, err := New(matrixString)

    if err != nil {
		t.Run("Rows and columns are not equal", func(t *testing.T) {
			assert.EqualError(t, err, "Rows need to be the same length")
		})
	}
}

func TestMatrixFormat(t *testing.T) {
    matrixString := `1 2 3
    4 5 a
    7 8 9`

    _, err := New(matrixString)

    if err != nil {
		t.Run("Matrix format is not correct, constains non number", func(t *testing.T) {
			assert.EqualError(t, err, "strconv.Atoi: parsing \"a\": invalid syntax")
		})
	}
}

func TestMatrixRows(t *testing.T) {
    matrixString := `1 2 3
    4 5 6
    7 8 9`

    newMatrix, _ := New(matrixString)

    t.Run("matrix number of rows and row data", func(t *testing.T) {
        assert.Equal(t, newMatrix.rows, 3)
        assert.Equal(t, newMatrix.Rows()[0], []int{1, 2, 3})
        assert.Equal(t, newMatrix.Rows()[1], []int{4, 5, 6})
        assert.Equal(t, newMatrix.Rows()[2], []int{7, 8, 9})
	})
}

func TestMatrixCols(t *testing.T) {
    matrixString := `1 2 3
    4 5 6
    7 8 9`

    newMatrix, _ := New(matrixString)

    t.Run("matrix number of rows and row data", func(t *testing.T) {
        assert.Equal(t, newMatrix.cols, 3)
        assert.Equal(t, newMatrix.Cols()[0], []int{1, 4, 7})
        assert.Equal(t, newMatrix.Cols()[1], []int{2, 5, 8})
        assert.Equal(t, newMatrix.Cols()[2], []int{3, 6, 9})
	})
}

func TestMatrixSet(t *testing.T) {
    matrixString := `1 2 3
    4 5 6
    7 8 9`

    newMatrix, _ := New(matrixString)

    t.Run("matrix Set", func(t *testing.T) {
		ok := newMatrix.Set(8, 8, 17)
		assert.False(t, ok)

		ok = newMatrix.Set(2, 2, 17)
		assert.True(t, ok)
		assert.Equal(t, newMatrix.Rows()[2][2], 17)
	})
}
