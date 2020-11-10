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
  * Are encased in braces ({ ... })
  * Have a colon after the name in a name/value pair (:)
  * Containing multiple pairs separate pairs with a comma (,)
- Arrays:
  * Are encased in brackets ([ ... ])
  * Separate multiple items with commas (,)
- Whitespace technically doesn't matter, but objects and arrays tend to be structured with tabs.

## 1100 HCL2 
[Watch]()

00:08:38

While the majority of Packer templates you encounter currently will be written in JSON, HashiCorp has released beta support for HCL2, or HashiCorp Configuration Language, most commonly associated with HashiCorp's other product, Terraform. This is done with the intention of having HCL take over from JSON as the primary configuration language for Packer.

HCL itself is JSON-compatible, working as a "more human-readable" version than JSON's machine-friendly formatting.

As with JSON, HCL is also made up of objects and arrays, although there are differences to the presentation. Where JSON relied on its objects always being encased in braces, HCL takes a more simplified approach, allowing for object blocks to first define a type, then provide attributes in simple name = "value" format, eliminating excessive quotation marks.

So this JSON object:

```
{
  "builders": [
    {
      "ami_name": "packer-test",
      "region": "us-east-1",
      "instance_type": "t2.micro"
    }
  ]
}
```

Would become this in HCL:

```
source "amazon-ebs" "example" {
  ami_name = "packer-test"
  region = "us-east-1"
  instance_type = "t2.micro"
}
```

With source working as the type — the equivalent of defining the builders object above.

Arrays, in contrast, work essentially the same, but instead of being leveraged to list multiple of any Packer component, lists are instead reserved for any lists in the attributes of a template. Lists can also be assigned in HCL by repeating the object name — this will add an item, not overwrite it:

```
service {
    key = "value"
}

service {
    key = "value"
}
```

While the two core structures of a template remain the same in HCL as JSON, HCL also leverages a few different concepts and terms: attributes, blocks, and bodies.

Attributes are a single configuration unit, such as ami_name = "packer-test", whereas blocks are a collection of these units, annotated with a block type, which we've already discussed. Finally, a collection of related blocks is a body. A template can comprise a single body or multiple, depending on the goals of the template.

Finally, one primary benefit of using HCL is the ability to add comments natively. Since we'll be using Packer to write templates — templates that will undoubtedly be used by others — leaving comments when needed can be valuable to our templating. In fact, I struggled with annotating some of the initial JSON lesson because I couldn't use comments!

***Wrap Up***
- HCL also uses objects and arrays.
  * Objects use a simplified structure:
    - Assign name/value pairs with an equal sign (=), not a colon (:)
    - No commas
    - Names are unquoted
  * Arrays remain mostly the same; can also be assigned via repeated object names
- HCL templates are made up of:
  * Attributes, which configure a single piece of the template
  * Blocks, which comprise attributes assigned an overall type
  * Bodies, which are made of related blocks

## 1200 Hands-On Lab: Formatting a Packer Template in JSON 

00:15:00

## 1300 Hands-On Lab: Formatting a Packer Template in HCL2 

00:10:00
