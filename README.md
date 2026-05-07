# assginment12

```


LinkedList* deleteAtLinkedList(LinkedList* li, int at) {
	if (at >= 0 && at < li->size) {
		PointType* nPtr = li->head;

		for (int i = 0; i < at - 1; i++) {
			nPtr = nPtr->next;
		}

		if (at == 0) {
			PointType* fPtr = li->head;
			li->head = fPtr->next;
			free(fPtr);
			
		}
		else {
			PointType* fPtr = nPtr->next;
			nPtr->next = fPtr->next;
			free(fPtr);
			
		}
	}
}
```

1. 기존에는 메모리를 free한 후 사이즈를 줄이지 않아 첫 번째 if에 조건이 계속 들어갑니다.
2. 일단 반복문 for를 at까지 반복합니다. 그러면 nPtr이 가르키는 주소는 at까지 가버립니다(nptr->next로 다음 주소로 가기 때문).
2-2.  그러면 수업에서 설명하셨던 것 처럼 지우려면 원하는 주소의 전 주소로 가야 하는데 지우려 하는 주소로 가게 됩니다.
   2-3결국 지우는 값이 1이상이 되어버리면 at의 값이 지우는 게 아닌 at이 가르키는 nptr->next의 값을 지웁니다.

수정한 곳은 반복문 for의 반복 횟수 조정(at -> at - 1), 삭제한 후 li의 사이즈를 1만큼 줄이는 li->size--;를 추가했습니다(print할 때에 size를 쓰기 때문).
