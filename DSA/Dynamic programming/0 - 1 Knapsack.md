### Recursive code :
```c++
int ks(int [] val, int [] wt, int w, int n){
	if(n == 0 || w == 0){
		return 0;
	}

	if(wt[n-1] <= w){
		return max(
			val[n-1] + ks(val, wt, w-wt[n-1], n-1),
			ks(val, wt, w, n-1) 
		);
	}
	else{
		return ks(val, wt, w, n-1);
	}
}
```

### Memoization
```c++
int t[n+1][w+1];
memset(t, -1, t.size());
for(int i=0; i<n+1; i++){
	for(int j=0; j++){
		if(i==0 || j==0)
			t[i][j] = 0;
	}
}

int ks(int [] val, int [] wt, int w, int n){
	if(n == 0 || w == 0){
		return 0;
	}

	if(t[n][w] != -1){
		return t[n][w]
	}
	
	if(wt[n-1] <= w){
		t[n][w] = max(
			val[n-1] + ks(val, wt, w-wt[n-1], n-1),
			ks(val, wt, w, n-1) 
		);
	}
	else{
		t[n][w] = ks(val, wt, w, n-1);
	}
	return t[n][w];
}
```

### Tabulation
```cpp

```
