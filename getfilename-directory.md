```
const char* get_filename_directory(const char* filename)
{
    char* ret = NULL;
    char dir[1024];
    char* cur = NULL;
    if(filename == NULL) return NULL;
    
#if defined(WIN32) && !defined(__CYGWIN__)
#   define IS_SEP(ch) ((ch=='/')||(ch=='\\'))
#else
#   define IS_SEP(ch) (ch=='/')
#endif
    
    strncpy(dir, filename, 1023);
    dir[1023] = 0;
    cur = &dir[strlen(dir)];
    while (cur > dir) {
        if (IS_SEP(*cur)) break;
        cur--;
    }
    if(IS_SEP(*cur))
    {
        if (cur == dir)
        {
            dir[1] = 0;
        }else {
            *cur = 0;
        }
        ret = strdup(dir);
    }else {
        if( getcwd(dir, 1024) != NULL)
        {
            dir[1023] = 0;
            ret = strdup(dir);
        }
    }
    
#undef IS_SEP
    return ret;
}
```



