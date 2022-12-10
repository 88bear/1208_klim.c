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
        int cnt=0;
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

char *int2bin(int n) { 
    // determine the number of bits needed ("sizeof" returns bytes) 
    int nbits = sizeof(n) * 8; 
    char *s = malloc(nbits+1);  // +1 for '\0' terminator 
    s[nbits] = '\0'; 
 
    // forcing evaluation as an unsigned value prevents complications 
    // with negative numbers at the left-most bit 
    unsigned int u = *(unsigned int*)&n; 
 
    int i; 
    unsigned int mask = 1 << (nbits-1); // fill in values right-to-left 
    for (i = 0; i < nbits; i++, mask >>= 1) 
        s[i] = ((u & mask) != 0) + '0'; 
 
    return s; 
} 
int main(void) { 
    printf("Your integers are %zu bits wide.\n\n", sizeof(int)*8); 
    int nums[13] = { 0, 1, 2, 3, -1, -2, -3, 31, 32, 255, 256, 8191, 8192 }; 
    int i; 
    for (i = 0; i < 13; i++) { 
        char *s = int2bin(nums[i]); 
        printf("%d -> %s\n", nums[i], s); 
        free(s); 
    } 
    return 0; 
} 

```
