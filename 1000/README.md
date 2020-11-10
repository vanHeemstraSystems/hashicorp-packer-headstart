# 1000 Packer

## 1000 What Is Packer? 
[Watch](https://linuxacademy.com/cp/courses/lesson/course/6824/lesson/1/module/612)

00:03:38

Packer is a tool for building machine images — or "compute" resources that store configuration, metadata, and permissions information for the creation of a virtual machine. Packer works cross-platform, which means we can create machine images for everything from cloud platform, like AWS, to old-school virtualization tools, like VirtualBox.

Packer does this by leveraging the tools we already use, such as our cloud platform APIs, and current configuration management tools. This means outside of learning how to write JSON- or HCL2-based Packer templates, any concepts we're introduced to won't necessarily be new — we just need to learn how to use them within our Packer template.

Packer will then take any templates we provide and produce an image, sending it straight to the appropriate platform just by running a single command.

***Wrap Up***
- Packer lets us create machine images.
- Machine images are roadmaps for virtual machine creation, ensuring our VM provisions with the appropriate configurations.

## 1100 Why Use Packer? 
[Watch](https://linuxacademy.com/cp/courses/lesson/course/6824/lesson/2/module/612)

00:04:03

Now that we know what Packer does, you might be wondering why we would use it over, say, spinning up a virtual machine and configuring the machine image that way. The answer lies in automation and the current tech landscape that values continuous integration and delivery. Packer — much like the configuration management programs you know and love — lets us write our desired outcome via text file. This doesn't just mean removing the need to access a VM itself to create a machine image — this also means we can create multiple machine images, as well as automate the creation, testing, and release of these images.

Additionally, Packer lets us achieve the dev/prod parity and multi-cloud environment of our dreams by allowing us to configure our machine image to work cross-platform in a single template. This way, the end result will be the same even if we're creating a Docker image for our developers and an Amazon Machine Image for production.

***Wrap Up***
- Packer removes the need to individually configure machine images in favor of writing templates.
- Packer templates fit in with existing automation pipelines.
- Packer lets us work cross-platform and cross-environment — all with a single configuration.

## 1200 Packer Breakdown 
[Watch](https://linuxacademy.com/cp/courses/lesson/course/6824/lesson/3/module/612)

00:05:36
