# 分治算法：快速排序

#include<iostream>
#include<ctime>
using namespace std;

void fast(int *a,int p,int q){
	if (p < q){
		int i = p;
		int j = q;
		int tmp = a[i];
		while (i < j){
			while (i<j&&a[j] >= tmp){
				j--;
			}
			a[i] = a[j];
			while (i<j&&a[i] < tmp){
				i++;
			}
			a[j] = a[i];
		}
		a[i] = tmp;
		fast(a, p, i - 1);
		fast(a, i + 1, q);
	}

}

int main(){
	clock_t start_time = clock();
	clock_t end_time;
	const int n = 100;
	int a[n];
	for (int i = 0; i < n; i++){
		a[i] = rand() % 100+1;
	}
	//int a[] = {45,3,32,10,8,77};
	//int len = sizeof(a)/4;
	fast(a,0,n-1);
	for (int i = 0; i < n; ++i){
		cout << a[i] << ' ';
	}
	cout << endl;
	end_time = clock();
	cout << "time:"<<end_time - start_time << endl;
	system("pause");
	return 0;
}
