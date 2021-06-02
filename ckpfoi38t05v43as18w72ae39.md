## Understanding Node.js File System basic ops for beginners.


In this article, I’ll be demonstrating you the way, you can use **File System** to deal with **files** related operations in **Node.js**. There are various instances when we need to deal with the files & perform **basic operations** such as Creating, Reading, Updating, Deleting & Renaming. Well, we’ll be covering all of these basic operations in this article. Let’s first understand the nature of File System module -

File System is a **built-in** Node.js module & can be imported into the project like this -

*var fs = require(‘fs’);*

All the methods in this module have **synchronous** as well as **asynchronous** forms. Asynchronous methods take **first parameter** of the **callback** function as an **error** and the **last parameter** as the **completion** callback. Let’s see through an example -

```
**function fileHandler() {
  
    fs.readFile('testFile.txt', 'utf8', (error, data) => {
      
        if (error) throw error;**

        console.log(data);
      
    })
  
}
```


In the above shown example, we can see that the callback function has two parameters i.e **error** & **data**. The first parameter is used to catch any **error** that occurs & the second parameter returns the **response**/**data** after successful execution of the function. Now that we’ve understood the basic usage & nature of File System module, let’s move on to implement some basic operations.

1. **Creating a new file.**

```
**function fileHandler() {
  
    fs.open('testFile.txt', 'w', (error) => {
      
        if (error) throw error;**

        console.log('File created!');
      
    });
  
}
```


In the above shown example, we’re using **fs.open()** method to create a **new** file. The **first** argument it takes is **name** of the file. In **second** argument, a **flag** has to be defined. If the flag is **w** for **writing**, the specified file is opened for **writing**. Other flags that could be used here include -

1. **r :** Opens the file for reading.

1. **r+** : Opens the file for reading and writing.

1. **rs :** Opens the file for reading in synchronous mode.

1. **w :** Opens the file for writing.

1. **a :** Opens the file for appending.

1. **a+ :** Opens the file for reading & appending.

Okay, now let’s **edit** our newly created file & add a few lines into it before proceeding to check next operations.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1622650979067/VMTqWzC_C.jpeg)

2. **Updating a file.**

Now, let’s check how can we **update** an **existing** file & **append** data to it.

```
**function fileHandler() {
  
    fs.appendFile('testFile.txt', 'This line is beyond the end.', (error) => {
      
        if (error) throw error;**

        console.log('Data has been added!');
      
    });
  
}
```


In the above shown example, we’re using **.append()** method to **append** data to the **end** of an **existing** file. As the **first** argument, it takes the target file **name** & as the **second** argument, it takes **data** to be appended in the end. Let’s see the outcome for the above shown example :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1622650980372/m5c3_SRCw.jpeg)

There’s another way for updating the content of a file using **.writeFile()** method. So, how is **.append()** different from **.writeFile()** ? Well, in case of **.append()**, we add content at **end** of the existing data. However, in case of **.writeFile()**, the existing content gets **replaced** by new specified content. Let’s try that out.

```
**function fileHandler() {
  
    fs.writeFile('testFile.txt', "I'm the replacement you've been looking for.", (error) => {
      
        if (error) throw error;**

        console.log('Content has been replaced!');
      
    });
  
}
```


In **.writeFile()** method, the way of passing the arguments is similar to that of **.append()** method. Let’s check its output :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1622650981940/bDyC2dc53.jpeg)

In the above shown output, you can see that the **.writeFile()** method has completely **replaced** the existing file content with the one specified in its second argument.

3. **Reading a file**

To read a file using **fs** module, we can use **.readFile()** method. It takes **name** of the target file as its **first** argument, an **encoding format** as its **second**. Its callback function returns **error** & **data** read from the file. Let’s check it out -

```
**function fileHandler() {
  
    fs.readFile('testFile.txt', 'utf8', (error,data) => {
      
        if (error) throw error;**

        console.log('------- [File Data] -------');
      
        console.log(data);
      
        console.log('--------- THE END ---------');
      
    });
  
}
```


Let’s check the output for above demonstrated example -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1622650983233/SWmEpUwiP.jpeg)

Looks good? Right? So, this way, we can **read** the content of a file using **.readFile()** method.

4. **Renaming a file**

```
**function fileHandler() {
  
    fs.rename('testFile.txt', 'newTestFile.txt', (error) => {
      
        if (error) throw error;**

        console.log('File renamed successfully!');
      
    });
  
}
```


In the above shown example, it is shown that how can we **rename** a file using **.rename()** method. The **first argument** it takes is **name** of the target file & as second argument, it takes the **new name**. This function successfully **changes** the filename from **testFile.txt** to **newTestFile.txt**.

5. **Deleting a file**

```
**function fileHandler() {
  
    fs.unlink('testFile.txt', (error) => {
      
        if (error) throw error;**

        console.log('File deleted successfully!');
      
    });
  
}
```


In this example, we can see how a file can be **deleted** using **.unlink()** method. After the execution of this function, the specified file i.e **dataFile.txt** is successfully deleted.

So, that’s all about the **file system** module & its basic operations. I hope I’ve made things **simpler** for you to understand. If you feel you’ve gained something from this article & such simplified articles should keep coming, kindly consider supporting me by donating at [paypal.me/topcoded](https://www.paypal.me/topcoded). Kindly give your **feedback** that’d help me to bring better & simplified content for you. Thanks for reading! See you in the next one.