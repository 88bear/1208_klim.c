# sort_struct_klim.c

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
#include <stdlib.h>

not done yet

```
