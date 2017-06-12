```
const char* get_filename(const char*filename)
{
    const char* backslashed = strrchr(filename, '/');
    if (!backslashed || backslashed == filename) return filename;
    
    const char* filenameWithExt = backslashed+1;
    return  filenameWithExt;
}
```



