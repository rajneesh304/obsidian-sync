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
memset(t, -1, t.size())

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
