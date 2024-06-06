package main

import "fmt"

func isLeapYear(year int) bool {
	if year%4 == 0 && year%100 != 0 {
		return true
	}
	if year%400 == 0 {
		return true
	}
	return false
}

func printHeader() {
	fmt.Println("    Mon Tue Wed Thu Fri Sat Sun")
}

func firstDayOfYear(year int) int {
	a := 2
	for i := 1924; i < year; i++ {
		if isLeapYear(i) {
			a += 2
		} else {
			a++
		}
	}
	if a%7 == 0 {
		return 7
	}
	return a % 7
}

func monthDays(year, month int) int {
	days := []int{0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}
	if month == 2 && isLeapYear(year) {
		return 29
	}
	return days[month]
}

func firstDayOfMonth(year, month int) int {
	i := firstDayOfYear(year)
	first := []int{0, i, (i + 3) % 7, (i + 3) % 7, (i + 6) % 7, (i + 1) % 7, (i + 4) % 7, (i + 6) % 7, (i + 2) % 7, (i + 5) % 7, i, (i + 3) % 7, (i + 5) % 7}
	for m := 1; m <= 12; m++ {
		if first[m] == 0 {
			first[m] = 7
		}
	}
	return first[month]
}

func firstDayOfMonthLeap(year, month int) int {
	i := firstDayOfYear(year)
	first := []int{0, i, (i + 3) % 7, (i + 4) % 7, i % 7, (i + 2) % 7, (i + 5) % 7, i % 7, (i + 3) % 7, (i + 6) % 7, (i + 1) % 7, (i + 4) % 7, (i + 6) % 7}
	for m := 1; m <= 12; m++ {
		if first[m] == 0 {
			first[m] = 7
		}
	}
	return first[month]
}

func printMonth(year, month int) {
	n := monthDays(year, month)
	var f int
	if isLeapYear(year) {
		f = firstDayOfMonthLeap(year, month)
	} else {
		f = firstDayOfMonth(year, month)
	}
	printHeader()
	for i := 1; i < f; i++ {
		fmt.Print("    ")
	}
	for day := 1; day <= n; day++ {
		fmt.Printf("%4d", day)
		f++
		if f > 7 {
			f = 1
			fmt.Println()
		}
	}
	if f != 1 {
		fmt.Println()
	}
}

func main() {
	var year int
	fmt.Scan(&year)
	for month := 1; month <= 12; month++ {
		fmt.Printf("\n%d %d\n", year, month)
		printMonth(year, month)
	}
}
