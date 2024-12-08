![](attachment/f87270ef628e65adafea625ea187bca3.png)

# WHAT IS THE GET_NEXT_LINE FUNCTION ?

In this project, we were tasked with implementing the **get_next_line** function, which reads and returns a single line from a file referenced by a file descriptor `(fd)`, each time it is called thanks to the brilliant utilization of `static variables`, it is also an interesting concept we'll learn about during this task.

##### How it is prototyped:

```c
char  *get_next_line(int fd);
```


- Return value : the function returns a string `char *` , which is the line read from the file referenced by `(int fd)`

- Parameter : the get_next_line function takes a small positive integer as an argument when it is called, this [file descriptor](https://en.wikipedia.org/wiki/File_descriptor) is a reference point or a [handle](https://en.wikipedia.org/wiki/Handle_(computing)) to an open file within the system, it is passed as a signed integer to handle and manage errors in cases such as invalid or closed file descriptors, we'll dive more into this world of FDs in a bit.

**--> Now let's dive into the inner workings of our get_next_line function.**

**or as I would like to call it Get Next Train.**

---
# GET_NEXT_TRAIN. 

I built my logic around the idea of fetching departed trains, in this case our lines, from a station\
referenced by an address, where basically the station is the file we're reading from.\
and the address number is the file descriptor, which has the information needed for us to\
access the station (file).

What to keep in mind :\
Train : The line we read from the file.\
Address : The file descriptor number referencing the file.\
Station : The file we are reading from.

![](attachment/640d9c48502f74732032b896bf93fabe.png)

We will use these utility functions to help building the main get_next_line function:

- ft_substr : Cuts a string from a `start` position until `len` characters is reached and returns a pointer to the memory allocated sub string.
- ft_strjoin : Joins two strings together in a memory allocated string (concatenates).
- ft_strdup : duplicates a string and allocates memory for it on the heap.
- ft_strlen : calculates the length of a string.
- ft_strchr : locates a character, in our case `\n` within a string, if it finds it, it returns a pointer to that location, otherwise `null`.

---
#### Main function called --- > get_next_line (fd).

```c
char	*get_next_line(int fd)
{
	// Static variable to hold leftover data.
	// Line to return (char *)

	if (/*. Error handling cases. */)
	{
		// Error handling logic.
		return (NULL);
	}
	
	// function (1) to read data
	if (/*  Error while reading.  */)
		return (NULL);
	
	// function (2) to cut line to return 
	// function (3) to cut leftover data if there is any
	
	return (/* Line (departed_train) */);
}
```

Error handling has quite a bit of explaining in this project, let's first discuss the functions utilized in the GNL algorithm.

I used 3 helper functions in order to read a line from a file up until a new line.\
and as it follows our train analogy convention these are ...

##### load_train_car :

```c
static char	*load_train_car(int fd, char *train_head);
```

This function is responsible for reading the file chunk by chunk based on the specified buffer size until a new line is found, then it returns the read data in the form of a string `char *`.

##### serve_train_departure : 

```c
static char	*serve_train_departure(char *train_head);
```

This function is responsible for cutting the string (train) up until the first occurrence of a new line if there is any, if not it returns the entire line allocated that being the last line.

#### update_train_head :

```c
static char *update_train_head(char *train_head)
```

This function is responsible for cutting the line from the pointer to a new_line + 1, storing the leftover data in the static variable for later use, when the function is called again.






### IMPORTANT VARIABLES VISUALIZED : 

![](attachment/0047ab4fdd3e09be6eff4afacb10eed9.png)
