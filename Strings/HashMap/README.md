# HashMap

``` sh
/*******************************************************************
                            HashMap

    1.  The data structure used for storing key-value pairs

    2.  How to insert a key-value pair into a HashMap

    3.  How to search for a key in a HashMap

    4.  How to delete a key-value pair in a HashMap


                                             COMP9024 24T2

 *******************************************************************/
``` 


A HashMap is a fundamental data structure in programming that provides a way to store key-value pairs.

Internally, a HashMap uses an array of buckets to store key-value pairs. 

Each bucket is a linked list of elements. 

When multiple elements hash to the same bucket (collision), they are stored as nodes in this linked list.

The key’s hash code determines the bucket location for storage. 

Hashing is used to convert the key into an index in the underlying array.

| HashMap| 
|:-------------:|
| <img src="diagrams/OurHashMap.png" width="100%" height="100%"> |

### Capacity and Load Factor

The capacity of a HashMap's table refers to the number of buckets (or slots) available in the underlying array where the key-value pairs are stored.

Load factor is calculated as the ratio of the number of elements currently present in the HashMap to the capacity of the HashMap's table.

The load factor (e.g., default is 0.75 in [Java's HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)) determines when the HashMap will resize its capacity. 

When the number of elements exceeds the load factor multiplied by the current capacity, the HashMap will resize and rehash its elements into a larger table.

We assume that both the key and its corresponding value are C strings in this project.

## Basic Operations
```C

// Insertion: Adding a key-value pair to a HashMap
void HashMapPut(struct HashMap *pMap, const char* key, const char* value);

// Retrieval: Getting a value associated with a key
const char *HashMapGet(struct HashMap *pMap, const char* key);

// Deletion: Removing a key-value pair 
void HashMapDelete(struct HashMap *pMap, const char* key);

```



## 1 How to download this project in [CSE VLAB](https://vlabgateway.cse.unsw.edu.au/)

Open a terminal (Applications -> Terminal Emulator)

```sh

$ git clone https://github.com/sheisc/COMP9024.git

$ cd COMP9024/Strings/HashMap

HashMap$ 

```


## 2 How to start [Visual Studio Code](https://code.visualstudio.com/) to browse/edit/debug a project.


```sh

HashMap$ code

```

Two configuration files (HashMap/.vscode/[launch.json](https://code.visualstudio.com/docs/cpp/launch-json-reference) and HashMap/.vscode/[tasks.json](https://code.visualstudio.com/docs/editor/tasks)) have been preset.



#### 2.1 Open the project in VS Code

In the window of Visual Studio Code, please click "File" and "Open Folder",

select the folder "COMP9024/Strings/HashMap", then click the "Open" button.


#### 2.2 Build the project in VS Code

click **Terminal -> Run Build Task**


#### 2.3 Debug the project in VS Code

Open src/main.c, and click to add a breakpoint (say, line 34).

Then, click **Run -> Start Debugging**

### 2.4 Directory

```sh
├── Makefile             defining set of tasks to be executed (the input file of the 'make' command)
|
├── README.md            introduction to this project
|
├── src                  containing *.c and *.h
|   |
|   |
│   ├── HashMap.c        The data structure used for storing key-value pairs
│   ├── HashMap.h
|   |
│   └── main.c           main()
|
|── images               containing *.dot and *.png files
|
|── diagrams             containing *.png files
|
└── .vscode              containing configuration files for Visual Studio Code
    |
    ├── launch.json      specifying which program to debug and with which debugger,
    |                    used when you click "Run -> Start Debugging"
    |
    └── tasks.json       specifying which task to run (e.g., 'make' or 'make clean')
                         used when you click "Terminal -> Run Build Task" or "Terminal -> Run Task"
```

Makefile is discussed in [COMP9024/C/HowToMake](../../C/HowToMake/README.md).

## 3 The main procedure

### 3.1 make and ./main

**In addition to utilizing VS Code, we can also compile and execute programs directly from the command line interface as follows.**

``` sh

HashMap$ make

HashMap$ ./main
The meaning of "ear": the sense organ for hearing

Updating the meaning of "ear"
The meaning of "ear": The sense organ for hearing

HashMapDelete(pMap, "earl")

The hash map does not contain the key "earl"

	 ear: The sense organ for hearing
	 apply: put into service
	 ape: a large primate that lacks a tail
	 apes: the plural noun of the word ape
	 earth: the planet on which we live
	 east: the eastern part of the world
	 app: an application, especially as downloaded by a user to a mobile device
	 ace: a playing card with a single spot on it
	 early: happening or done before the usual or expected time
	 "earl" not found
	 aces: the plural noun of the word ace
	 apple: a round fruit with firm, white flesh and a green, red, or yellow skin

```


### 3.2 make view

**Ensure that you have executed 'make' and './main' before 'make view'.**


```sh
HashMap$ make view
```

**Click on the window of 'feh' or use your mouse scroll wheel to view images**.

Here, **feh** is an image viewer available in [CSE VLAB](https://vlabgateway.cse.unsw.edu.au/).

```C
// keys
static char *words[] = { 
    "ear", "apply", "ape", "apes", "earth", 
    "east", "app", "ace", "early", "earl", 
    "aces", "apple"
};
```

#### 3.2.1 HashMapPut()

| HashMapPut("ear", "the sense organ for hearing") | 
|:-------------:|
| <img src="images/OurHashMap_0000.png" width="100%" height="100%"> |

| HashMapPut("apply", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0001.png" width="100%" height="100%"> |

| HashMapPut("ape", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0002.png" width="100%" height="100%"> |

| HashMapPut("apes", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0003.png" width="100%" height="100%"> |

| HashMapPut("earth", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0004.png" width="100%" height="100%"> |



| HashMapPut("east", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0005.png" width="100%" height="100%"> |

| HashMapPut("app", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0006.png" width="100%" height="100%"> |

| HashMapPut("ace", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0007.png" width="100%" height="100%"> |

| HashMapPut("early", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0008.png" width="100%" height="100%"> |

| HashMapPut("earl", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0009.png" width="100%" height="100%"> |



| HashMapPut("aces", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0010.png" width="100%" height="100%"> |

| HashMapPut("apple", ...) | 
|:-------------:|
| <img src="images/OurHashMap_0011.png" width="100%" height="100%"> |


#### 3.2.2 HashMapDelete()

| HashMapDelete("earl") | 
|:-------------:|
| <img src="images/OurHashMap_0012.png" width="100%" height="100%"> |

## 4 Data structures

```C

#define BUCKET_COUNT    2
#define MAX_KEY_LEN     63
#define MAX_VAL_LEN     255

#define LOAD_FACTOR_THRESHOLD       0.75

struct BucketEntry {
    char key[MAX_KEY_LEN + 1];
    char value[MAX_VAL_LEN + 1];
    struct BucketEntry* next;
};

struct HashMap{
    /*
                             ------------------------
                                buckets[capacity-1]    ---->  BucketEntry  ----> ....   ---> BucketEntry
                                buckets[capacity-2]
                                     ...
            buckets   ---->     buckets[0]             ---->  BucketEntry  ----> ....   ---> BucketEntry 
                             ------------------------
                              Array of pointers on the heap
     */
    struct BucketEntry **buckets;
    // the number of slots/buckets in the HashMap
    int capacity;
    // the number of key-value pairs in the HashMap
    int n;
};

```


## 5 Algorithms

### 5.1 main()

```C
// keys
static char *words[] = { 
    "ear", "apply", "ape", "apes", "earth", 
    "east", "app", "ace", "early", "earl", 
    "aces", "apple"
};

// values
static char *meanings[] = { 
    "the sense organ for hearing", 
    "put into service", 
    "a large primate that lacks a tail", 
    "the plural noun of the word ape", 
    "the planet on which we live", 
    
    "the eastern part of the world",
    "an application, especially as downloaded by a user to a mobile device", 
    "a playing card with a single spot on it", 
    "happening or done before the usual or expected time", 
    "a British nobleman",
    
    "the plural noun of the word ace",
    "a round fruit with firm, white flesh and a green, red, or yellow skin"
}; 

int main(void) {
    long count = 0;
    struct HashMap *pMap = CreateHashMap();

    int n = sizeof(words)/sizeof(words[0]);
    assert(n == (sizeof(meanings)/sizeof(meanings[0])));   

    // create a sub-directory 'images' (if it is not present) in the current directory
    system("mkdir -p images");
    // remove the *.dot and *.png files in the directory 'images'
    system("rm -f images/*.dot images/*.png");

    for (int i = 0; i < n; i++) {
        HashMapPut(pMap, words[i], meanings[i]);
        //
        GenOneImage(pMap, "OurHashMap", "images/OurHashMap", count);
        count++;
    }

    // Demonstrate get and put
    const char *key = words[0];
    const char *value = NULL;
    value = HashMapGet(pMap, key);
    if (value) {
        printf("\nThe meaning of \"%s\": %s\n", key, value);
    }
  
    printf("\nUpdating the meaning of \"%s\"", key);
    if (value) {
        HashMapPut(pMap, key, "The sense organ for hearing");
    }

    value = HashMapGet(pMap, key);
    if (value) {
        printf("\nThe meaning of \"%s\": %s\n", key, value);
    }

    key = "earl";
    printf("\nHashMapDelete(pMap, \"%s\")\n", key);
    HashMapDelete(pMap, key);

    GenOneImage(pMap, "OurHashMap", "images/OurHashMap", count);
    count++;

    value = HashMapGet(pMap, key);
    if (!value) {
        printf("\nThe hash map does not contain the key \"%s\"\n\n", key);
    }

    for (int i = 0; i < n; i++) {
        value = HashMapGet(pMap, words[i]);
        if (!value) {
            printf("\t \"%s\" not found\n", words[i]);
        } else {
            printf("\t %s: %s\n", words[i], value);
        }        
    }

    ReleaseHashMap(pMap);
    return 0;
}
```

### 5.2 CreateHashMap()
```C
void ReleaseHashMap(struct HashMap* pMap) {
    for (int i = 0; i < BUCKET_COUNT; i++) {
        struct BucketEntry *current = pMap->buckets[i];
        // Release the linked list in each bucket
        while (current != NULL) {
            struct BucketEntry *tmp = current;
            current = current->next;
            free(tmp);
        }
    }
    free(pMap);
}



/*
    For more about hash functions, please refer to 

        https://cseweb.ucsd.edu/~kube/cls/100/Lectures/lec16/lec16.html
 */
static unsigned int GetHash(const char *key) {
    unsigned int sum = 0;
    for (int i = 0; key[i] != '\0'; i++) {
        sum += ((unsigned char) key[i]);
    }
    return sum;  
}

struct HashMap *CreateHashMap(void) {
    struct HashMap *pMap = (struct HashMap *) malloc(sizeof(struct HashMap));
    struct BucketEntry **buckets = 
        (struct BucketEntry **) malloc(sizeof(struct BucketEntry *) * BUCKET_COUNT);
    assert(pMap && buckets);

    pMap->buckets = buckets;
    pMap->capacity = BUCKET_COUNT;
    pMap->n = 0;
    for (int i = 0; i < pMap->capacity; i++) {
        pMap->buckets[i] = NULL;
    }    
    return pMap;
}

void ReleaseHashMap(struct HashMap* pMap) {
    for (int i = 0; i < pMap->capacity; i++) {
        struct BucketEntry *current = pMap->buckets[i];
        // Release the linked list in each bucket
        while (current != NULL) {
            struct BucketEntry *tmp = current;
            current = current->next;
            free(tmp);
        }
    }
    free(pMap->buckets);
    free(pMap);
}

```


### 5.3 HashMapPut()

```C

void HashMapPut(struct HashMap *pMap, const char* key, const char* value) {
    unsigned int index = GetHash(key) % pMap->capacity;
    struct BucketEntry *current = pMap->buckets[index];
    
    // Update the value if its key already exists
    while (current != NULL) {
        if (strcmp(current->key, key) == 0) {
            strncpy(current->value, value, MAX_VAL_LEN);
            current->value[MAX_VAL_LEN] = '\0';
            return;
        }
        current = current->next;
    }

    // Add a key-value pair
    struct BucketEntry *pEntry = (struct BucketEntry *) malloc(sizeof(struct BucketEntry));
    strncpy(pEntry->key, key, MAX_KEY_LEN);
    pEntry->key[MAX_KEY_LEN] = '\0';
    strncpy(pEntry->value, value, MAX_VAL_LEN);
    pEntry->value[MAX_VAL_LEN] = '\0';
    pEntry->next = pMap->buckets[index];
    pMap->buckets[index] = pEntry;
    //increase the number of key-value pairs
    pMap->n++;

    // Test whether we need to resize the HashMap for better performance
    if (HashMapLoadFactor(pMap) >= LOAD_FACTOR_THRESHOLD) {
        HashMapResize(pMap);
    }
}
```
### 5.4 HashMapGet()

```C

const char *HashMapGet(struct HashMap *pMap, const char* key) {
    unsigned int index = GetHash(key) % pMap->capacity;
    struct BucketEntry *current = pMap->buckets[index];
    
    while (current != NULL) {
        if (strcmp(current->key, key) == 0) {
            return current->value;
        }
        current = current->next;
    }
    // Not found
    return NULL; 
}

```

### 5.5 HashMapDelete()

```C

void HashMapDelete(struct HashMap *pMap, const char* key) {
    unsigned int index = GetHash(key) % pMap->capacity;
    struct BucketEntry *current = pMap->buckets[index];
    struct BucketEntry *prev = NULL;
    
    while (current != NULL) {
        if (strcmp(current->key, key) == 0) {
            if (prev != NULL) {
                prev->next = current->next;
            } else {
                pMap->buckets[index] = current->next;
            }
            free(current);
            // decrease the number of key-value pairs
            pMap->n--;
            return;
        }
        prev = current;
        current = current->next;
    }
}
```

### 5.6 HashMapResize()
```C
static void HashMapResize(struct HashMap *pMap) {
    int newCapacity = pMap->capacity * 2;
    struct BucketEntry **newBuckets = 
        (struct BucketEntry **) malloc(sizeof(struct BucketEntry *) * newCapacity);
    assert(newBuckets);
    for (int i = 0; i < newCapacity; i++) {
        newBuckets[i] = NULL;
    }

    // move the existing bucket entries 
    for (int i = 0; i < pMap->capacity; i++) {
        struct BucketEntry *current = pMap->buckets[i];
        while (current != NULL) {
            struct BucketEntry *tmp = current;
            unsigned int index = GetHash(tmp->key) % newCapacity;
            current = current->next;
            // insert the BucketEntry at the head of the linked list pointed to by newBuckets[index]
            tmp->next = newBuckets[index];
            newBuckets[index] = tmp;
        }
    }
    // release the old buckets
    free(pMap->buckets);
    pMap->buckets = newBuckets;
    pMap->capacity = newCapacity;
}

double HashMapLoadFactor(struct HashMap *pMap) {
    assert(pMap->capacity > 0);
    double loadFactor = ((double) (pMap->n)) / pMap->capacity;
    return loadFactor;
}

```

### 5.7 HashMapToDot()
```C

//////////////////////////// HashMap2Dot ////////////////////////////////////////

#define FILE_NAME_LEN  255

void GenOneImage(struct HashMap* pMap, char *graphName, char *fileName, long seqNo) {
    char dotFileName[FILE_NAME_LEN+1] = {0};
    char pngFileName[FILE_NAME_LEN+1] = {0};
    char command[(FILE_NAME_LEN+1)*4] = {0};
    
    snprintf(dotFileName, FILE_NAME_LEN, "%s_%04ld.dot", fileName, seqNo);
    snprintf(pngFileName, FILE_NAME_LEN, "%s_%04ld.png", fileName, seqNo);

    HashMap2Dot(pMap, dotFileName, graphName);

    snprintf(command, FILE_NAME_LEN*4, "dot -T png %s -o %s", dotFileName, pngFileName);

    //printf("%s\n", command);
    
    // Execute the command in a child process (fork() + exec() on Linux)
    system(command);
}

/*
    digraph OurHashMap {
    "HashMap_0x556d03a862a0_c=4_n=2"
    "HashMap_0x556d03a862a0_c=4_n=2" -> {"ear"} [label="0"]
    "HashMap_0x556d03a862a0_c=4_n=2" -> {"apply"} [label="2"]
    }
 */
void HashMap2Dot(struct HashMap* pMap, char *filePath, char *graphName) {
    
    FILE *dotFile = fopen(filePath, "w");
    assert(pMap);
    /*
        FIXME:  check sanity of the parameters.
     */
    if (dotFile) {
        char *edgeConnectorStr = "->";
        fprintf(dotFile, "digraph %s {\n", graphName);
        // Node for the whole HashMap
        fprintf(dotFile, 
                "\"HashMap_%p_c=%d_n=%d\"\n", 
                pMap,
                pMap->capacity,
                pMap->n);
        for (int i = 0; i < pMap->capacity; i++) {
            if (pMap->buckets[i]) {
                fprintf(dotFile, 
                        "\"HashMap_%p_c=%d_n=%d\" %s {\"%s\"} [label=\"%d\"]\n",
                        pMap,
                        pMap->capacity,
                        pMap->n,
                        edgeConnectorStr,
                        pMap->buckets[i]->key,
                        i);
                struct BucketEntry *next = pMap->buckets[i]->next;
                struct BucketEntry *current = pMap->buckets[i];
                while (next) {
                    fprintf(dotFile, 
                            "\"%s\" %s {\"%s\"}\n",
                            current->key,
                            edgeConnectorStr,
                            next->key);
                    current = next;
                    next = current->next;                   
                }
            }
        }
        fprintf(dotFile, "}\n");
        fclose(dotFile);
    }                
}
```

