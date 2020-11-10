# 1100 Template Languages

## 1000 JSON 
[Watch](https://linuxacademy.com/cp/courses/lesson/course/6825/lesson/1/module/612)

00:06:26

JSON is one of two languages supported by Packer and is by far the more mature. While slightly less human readable than HCL, JSON is currently the more stable option for writing Packer templates.

JSON data comprises two structures: objects and arrays. If you're familiar with any sort of data-serialization or programming language, you've undoubtedly encountered these structures before, although perhaps with other names, such as associative arrays, dictionaries, or key lists (objects); ordered lists, vectors, or sequences (arrays).

An object comprises a name/value pair. In JSON, objects begin with a left brace ({), end with a right brace (}), and the name portion of the name/value pair ends with a colon (:). An object of multiple pairs should separate the pair with a comma (,):

```
{
    "name": "value",
    "name": "value"
}
```

Or see an object in action with Packer:

```
"filters": {
      "virtualization-type": "hvm",
      "name": "ubuntu/images/*ubuntu-xenial-16.04-amd64-server-*",
      "root-device-type": "ebs"
    },
```

Objects can also contain our next structure: the array.

An array is just a list. In JSON, this list is contained in left and right brackets ([ ... ]), and multiple items are separated by commas (,):

```
[
    "item",
    "item"
]
```

In Packer, our arrays tend to be a little more involved — and they're always part of a greater object:

```
"provisioners": [
      {
          "type": "file",
          "source": "./welcome.txt",
          "destination": "/home/ubuntu/"
      },
      {
          "type": "shell",
          "inline":[
              "ls -al /home/ubuntu",
              "cat /home/ubuntu/welcome.txt"
          ]
      }
  ]
```

The above snippet contains two arrays: the overall provisioners array, which contains two objects for provisioning ("type": "file" and "type": "shell"); and the array assigned to the "inline" name-value pair, which lists two commands to run via the shell provisioner.

Finally, let's address whitespace — notably, that with JSON it doesn't really matter. That said, you'll notice in our examples that object and array data tends to be kept on new lines with structured tabbing. What you use for tabs is ultimately up to you, but HashiCorp tends to use four spaces in their documentation and this course will follow suit.

***Wrap Up***
- Packer templates can be written in JSON.
- JSON comprises objects and arrays.
- Objects:
: Are encased in braces ({ ... })
: Have a colon after the name in a name/value pair (:)
: Containing multiple pairs separate pairs with a comma (,)
- Arrays:
: Are encased in brackets ([ ... ])
: Separate multiple items with commas (,)
- Whitespace technically doesn't matter, but objects and arrays tend to be structured with tabs.

## 1100 HCL2 
[Watch]()

00:08:38

## 1200 Hands-On Lab: Formatting a Packer Template in JSON 

00:15:00

## 1300 Hands-On Lab: Formatting a Packer Template in HCL2 

00:10:00
