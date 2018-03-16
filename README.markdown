```
typedef int mr_utype;
typedef mr_utype mr_small;

typedef unsigned int mr_lentype;

struct bigtype
{
    mr_lentype len;
    mr_small *w;
};                

typedef struct bigtype *big;

typedef big zzn;

typedef struct
{
    big a;
    big b;
} zzn2;

typedef struct 
{
    int marker;
    zzn2 x;
    zzn2 y;
    zzn2 z;
} ecn2;
```
