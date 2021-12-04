# 指標應用：Swap


用指標來執行傳值變數的兩數交換（swap）：


```c
#include <stdio.h>
#include <stdlib.h>

void Swap(int*, int*);

int main(void)
{
	int firstCard = 10;
	int secondCard = 6;

	printf("未交換前，firstCard = %d, secondCard = %d 。\n", firstCard, secondCard);

	Swap(&firstCard, &secondCard);

	printf("  交換後，firstCard = %d, secondCard = %d 。\n", firstCard, secondCard);
}

void Swap(int* firstNumberPointer, int* secondNumberPointer)
{
	int temp = *firstNumberPointer;
	*firstNumberPointer = *secondNumberPointer;
	*secondNumberPointer = temp;
}

// Output:
//
// 未交換前，firstCard = 10, secondCard = 6 。
//   交換後，firstCard = 6, secondCard = 10 。

```