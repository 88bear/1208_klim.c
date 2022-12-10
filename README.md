# 1208_klim.c

## 看完請在心中默念我愛071 沒默念計概0分
------------
### sort.c
```c
#include <stdio.h>
#include <stdlib.h>

#define NAME_LEN  16
#define N_REC    100

typedef struct {
  char name [NAME_LEN];
  int age;
} Record;

int rec_cmp(const void *a,const void *b){
        Record* ps0 = (Record*) a;
        Record* ps1 = (Record*) b;
        if(strcmp(ps0->name, ps1->name) == 0){
                return ps1->age - ps0 ->age;
        }
        else
                return strcmp(ps0->name, ps1->name);
}

int main(){
        int cnt = 0;
        Record std1[N_REC];
        while(scanf("%s %d", std1[cnt].name, &std1[cnt].age) != EOF){
                cnt++;
        }
        qsort(std1,cnt,sizeof(Record),rec_cmp);
        printf("\n");
        for(int i = 0; i < cnt; i++){
                printf("%-15s:%5d\n", std1[i].name, std1[i].age);
        }
}
```

### bits.c

```c
#include <stdio.h>
#define N_INT    1024

void displayBits(unsigned int value){
    unsigned int displayMark = 1 << 31;
    for(unsigned int c = 1; c <= 32; ++c){
        putchar(value & displayMark ? '1' : '0');
        value <<= 1;
        if(c % 8 == 0 && c != 32) putchar(' ');
    }
    putchar('\n');
}
int main(){
    int newNumA = 0, newNumB = 0;
    int numA[N_INT],numB[N_INT];
    int A = 0, B = 0;
    while(scanf("%d%d", &A, &B) != EOF){
        if(A == 0 && B == 0) break;
        for(int i = 0; i < A; ++i){
            scanf("%d", &numA[i]);
        }
        for(int i = 0; i < B; ++i){
            scanf("%d", &numB[i]);
        }
        for(int i = 0; i < A; ++i){
            newNumA = (1 << numA[i]) | newNumA;
        }
        for(int i = 0; i < B; ++i){
            newNumB = (1 << numB[i]) | newNumB;
        }
        printf("first  set : "); displayBits(newNumA);
        printf("second set : "); displayBits(newNumB);
        printf("union      : "); displayBits(newNumA|newNumB);
        printf("xor        : "); displayBits(newNumA^newNumB);
        newNumA = 0; newNumB = 0;
    }
    return 0;
}

```
