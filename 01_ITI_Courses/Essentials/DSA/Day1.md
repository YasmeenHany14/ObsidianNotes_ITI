# Algorithms
## Analysis of algorithms
* We calculate by unites,
* We calculate cost and time => No of units = sum cost * sum time
	* Cost => No of operation
	* Time => times of execution

``` cpp
int i = 0; //      cost 1 time 1
int sum = 0; //    cost 1 time 1
while(i <= n) { // cost 1 time n + 1 
	i+= 1; //      cost 2 time n
	sum += i; //   cost 2 time n
}

// total cost 1 + 1 + n + 1 + 2n + 2n => prop to n
```

* i++ is one op while i+=1 is 2 op
``` cpp
int sum = 0, i; //           cost 1 time 1
for(i = 0; i < n; i++)// cost 1 time 1 + cost 2 time n + cost 1 time 1
	sum += A[i];          // cost 2 time n
return sum;               // cost 1 time 1
```

# Sorting algorithms
## Selection sort
* Worst case => O(n2)
``` cpp
for(int i = 0; i < sz - 1; i++) {
	int minIdx = arr[i];
	for(int j = i + 1; j < sz; j++) {
		if(arr[j] < arr[minIdx])
			minIdx = j;
	}
	if (i != minIdx)
		swap(arr[i], arr[minIdx]);
}
```

## Bubble sort
* O(n2)
``` cpp
for(int i = 0; i < sz; i++)
	for(int j = i + 1; j < sz - i; j++)
		if(arr[j] < arr[i])
			swap(arr[i], arr[j]);
```

## Insertion sort
* Preferred with small datasets
* Similar to bubble, it compares each element with all before it

``` cpp
for(int i = 0; i < sz; i++) {
	for(int j = ) {
		if(arr[i] > arr[k])
	}
}
```

## Merge sort

## Quick sort

