package coverage

import (
	"os"
	"testing"
	"time"
	"errors"
	"strconv"
	"reflect"
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
	people := People{}

	for i := 0; i < 5; i++ {
		people = append(people, Person{})
	}

	if people.Len() != 5 {
		t.Errorf("Error: Length of slice should be equal to 5")
	}

}

func TestLess(t *testing.T) {
	var people People
	now := time.Time{}

	people = append(people, Person{"Tom", "York", now.AddDate(-2, 1, 3)})
	people = append(people, Person{"Tom", "York", now})
	people = append(people, Person{"Diana", "York", now})
	people = append(people, Person{"Diana", "York", now})

	if people.Less(0, 1) {
		t.Errorf("Error: Less by Birthday")
	}
	if people.Less(1, 2) {
		t.Errorf("Error: Less by FirstName")
	}
	if people.Less(2, 3) {
		t.Errorf("Error: Less by LastName")
	}

}

func TestSwap(t *testing.T) {
	var people People
	now := time.Time{}

	person_1 := Person{"Mary", "Kuratnik", now}
	person_2 := Person{"Diana", "Kuratnik", now}


	for _, person := range []Person{person_1, person_2} {
		people = append(people, person)
	}

	people.Swap(0, 1)

	if people[0] != person_2 || people[1] != person_1 {
		t.Errorf("Error: Ircorrect Swapp")
	}
}

func TestNew(t *testing.T) {

	matrix, err := New("12 4 \n 3")
	if err.Error() != "Rows need to be the same length" {
		t.Errorf("Error: Bad Matrix")
	}

	matrix, err = New("15 5 \n 3 1")
	expected := &Matrix{2, 2, []int{15, 5, 3, 1}}

	condition_1 := matrix.cols != expected.cols || matrix.rows != expected.rows
	condition_2 := !reflect.DeepEqual(matrix.data, expected.data)

	if condition_1 || condition_2 {
		t.Errorf("Error: Empty Matrix")
	}

	matrix, err = New("..")
	if !errors.Is(err, strconv.ErrSyntax) {
		t.Errorf("Error: Bad Matrix")
	}
}

func TestRows(t *testing.T) {
	matrix := &Matrix{3, 3, []int{1, 2, 3, 4, 5, 6, 7, 8, 9}}
	expected := [][]int{{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}

	actual := matrix.Rows()

	if !reflect.DeepEqual(actual, expected) {
		t.Errorf("Error: Irrcorrect matrix representantion")
	}
}

func TestCols(t *testing.T) {
	matrix := &Matrix{3, 3, []int{1, 2, 3, 4, 5, 6, 7, 8, 9}}
	expected := [][]int{{1, 4, 7}, {2, 5, 8}, {3, 6, 9}}

	columns := matrix.Cols()

	if !reflect.DeepEqual(columns, expected) {
		t.Errorf("Error: Irrcorrect matrix representantion")
	}
}

func TestSet(t *testing.T) {
	matrix := &Matrix{3, 3, []int{1, 2, 3, 4, 5, 6, 7, 8, 9}}
	expected := []int{1, 2, 2, 4, 5, 6, 7, 8, 9}

	is_set_value_1 := matrix.Set(0, 2, 2)
	is_set_value_2 := matrix.Set(-1, 2, 2)

	if is_set_value_2 || !is_set_value_1 || !reflect.DeepEqual(matrix.data, expected) {
		t.Errorf("Error: Ircorrect behavior")
	}

}