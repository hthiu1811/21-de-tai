# 21-de-tai
homework 
#include <stdio.h>
#include<iostream>
#include<conio.h>
using namespace std;
//HAM TIM KIEM NHI PHAN SU DUNG GIAI THUA DE QUY
int binarySearch(int arr[], int l, int r, int x)
{
   if (r >= l)
    {
        int mid = (l + r) / 2; //vị trí ở giữa
      // Nếu arr[mid] = x, trả về vi tri và kết thúc.
      if (arr[mid] == x)
           return mid;
        // Nếu arr[mid] > x, thực hiện tìm kiếm nửa trái của mảng
        if (arr[mid] > x)
            return binarySearch(arr, l, mid - 1, x);
        // Nếu arr[mid] < x, thực hiện tìm kiếm nửa phải của mảng
        return binarySearch(arr, mid + 1, r, x);
    }

    // Nếu không tìm thấy
    return -1;
}
int main(void)
{
    int arr[] = { 2, 3, 4, 10, 40 };    int n = sizeof(arr) / sizeof(arr[0]);
    int x = 10;
   int result = binarySearch(arr, 0, n - 1, x);
   if (result == -1)
        printf("Khong tim thay phan tu %d trong mang", x);
    else
        printf("%d xuat hien tai vi tri so %d", x, result);
  return 0;
}

//HAM TIM KIEM TUYEN TINH

int linear_search(int A[], int n, int x) {
    int i;
    for (i = 0; i < n; i++)
        //Neu co phan tu A[i] nao co gia tri bang voi x
        if (A[i] == x) {
            return i; //Tra ve vi tri phan tu duoc tim thay
        }
    return -1; //Khong tim thay phan tu trong mang A[]
}
int main() {
    //Khai bao bien n lam so luong phan tu mang
    int n = 4;
    //Khai bao mang gom cac phan tu
    int A[n] = { 2, 3, 4 ,10, 40 };
    //Khai bao gia tri can tim trong mang A
    int x = 20;
    //Khai bao bien index de nhan ket qua tim kiem duoc tra ve tu ham linear_search(A,n,x)
    int index = linear_search(A, n, x);
    //Neu ket qua index bang -1
    if (index == -1) {
        printf("Khong tim thay phan tu x = %d", x);
    }
    else { //Nguoc lai, neu index khong bang -1
        printf("Tim thay x = %d tai vi tri %d", x, index);
    }
}

//PHUONG PHAP DOI CHO TRUC TIEP DE SAP XEP

//Hàm đổi chỗ 2 số nguên a,b
void Swap(int& a, int& b)
{
    int temp = a;
    a = b;
    b = temp;
}
//Hàm sắp xếp Interchange Sort( DOI CHO TRUC TIEP )
void InterchangeSort(int a[], int n)
{
    for (int i = 0; i < n - 1; i++)
        for (int j = i + 1; j < n; j++)
            if (a[i] > a[j]) //Thực hiện đổi chỗ phần tử nhỏ hơn với phần tử thứ i.
                Swap(a[i], a[j]);
}
//hàm xuất mảng
void printArray(int arr[], int size)
{
    int i;
    for (i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}
int main()
{
    int arr[] = { 41, 23, 4, 14, 56, 1 };
    int n = sizeof(arr) / sizeof(arr[0]);
    InterchangeSort(arr, n);
    printf("Sorted array: \n");
    printArray(arr, n);
    return 0;
}

// HAM SAP XEP CHON TRUC TIEP DE SAP XEP

void Selection_Sort(int a[], int n)
{
    int min;//vị trí phần tử nhỏ nhất trong dãy hiện hành
    for (int i = 0; i < n - 1; i++)
    {
        min = i;
        for (int j = i + 1; j < n; j++)
        {
            if (a[j] < a[min])
            {
                min = j;//ghi nhận vị trí phần tử nhỏ nhất
            }
        }
        swap(a[min], a[i]);
    }
}
int main()
{
    int a[6] = { 41, 23, 4, 14, 56, 1 };
    Selection_Sort(a, 6);
    cout << "Mang sau khi sap xep:" << endl;
    for (int i = 0;i < 6;i++) {
        cout << a[i] << " ";
    }
    system("pause");
}

//HAM SAP XEP CHEN TRUC TIEP DE SAP XEP 

void Insertion_Sort(int a[], int n)
{
    int pos, i;
    int x;//lưu giá trị a[i] tránh bị ghi đè khi dời chỗ các phần tử
    for (i = 1; i < n; i++)
    {//đoạn a[0] đã sắp xếp
        x = a[i]; pos = i - 1;
        //tìm vị trí chèn x
        while ((pos >= 0) && (a[pos] > x))
        {
            //kết hợp dời chỗ các phần tử sẽ đứng sau x trong danh sách mới
            a[pos + 1] = a[pos];
            pos--;
        }
        a[pos + 1] = x;//chèn x vào danh sách
    }
}
int main()
{
    int a[6] = { 41, 23, 4, 14, 56, 1  };
    Insertion_Sort(a, 6);
    cout << "Mang sau khi sap xep:" << endl;
    for (int i = 0;i < 6;i++)
    {
        cout << a[i] << " ";
    }
    system("pause");
}

//HAM SAP XEO NHANH DE SAP XEP

void swap(int& a, int& b)
{
    int t = a;
    a = b;
    b = t;
}

int partition(int arr[], int low, int high)
{
    int pivot = arr[high];  
    int left = low;
    int right = high - 1;
    while (true) {
        while (left <= right && arr[left] < pivot) left++;
        while (right >= left && arr[right] > pivot) right--;
        if (left >= right) break;
        swap(arr[left], arr[right]);
        left++;
        right--;
    }
    swap(arr[left], arr[high]);
    return left;
}

//Hàm thực hiện giải thuật quick sort 
void quickSort(int arr[], int low, int high)
{
    if (low < high)
    {
        /* pi là chỉ số nơi phần tử này đã đứng đúng vị trí và là phần tử chia mảng làm 2 mảng con trái & phải */
        int pi = partition(arr, low, high);

        // Gọi đệ quy sắp xếp 2 mảng con trái và phải
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
//Hàm xuất mảng 
void printArray(int arr[], int size)
{
    int i;
    for (i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main()
{
    int arr[] = { 41, 23, 4, 14, 56, 1  };
    int n = sizeof(arr) / sizeof(arr[0]);
    quickSort(arr, 0, n - 1);
    printf("Sorted array: ");
    printArray(arr, n);
    return 0;
}
