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

The majority of work we do with Packer will be contained in the templates we write. Before we start writing these, however, let's take the time to ensure we have the basic vocabulary and structuring information we need to succeed.

A Packer template, at the very least, must have a builder assigned to it. A builder is what defines the platform we wish to build our image on, as well as any base configurations we need to work with that platform, such as API keys or image destinations.

We can then define our various desired configurations for our image with a provisioner (or multiple provisioners!). If you're already using configuration management to enforce state on your servers, then Packer works with this as well, offering provisioners for all major configuration management platforms (as well as some less common). We also have the option to provide shell scripts and upload files directly, if we're working outside the scope of config management.

Finally, once the build is done, we may want to provide instructions on what to do with the image itself or any other artifacts (which are the end result of a build). For this, we can add a post-processor. Post-processors tend to be closely tied to the builder — we wouldn't use the Amazon Import post-processor with the Microsoft Azure builder, for example.

And all of this work is done via Packer through the use of a communicator. If working exclusively on *nix-based hosts, this isn't something you'll need to worry about — SSH is the default communicator and works in the majority of instances. However, if we're using Packer to provision Windows, we will need to switch this to the winrm communicator.

These components are combined in our template to create a build — or a single machine image. A template can contain multiple builds that each produce their own machine image.

And once our template is all finished? We'll leverage the packer command on the CLI to launch our image — this will work like any other command line command.

***Wrap Up***
- Packer templates comprise builders, provisioners, post-processors, and communicators.
- Builders provide Packer platform configurations.
- Provisioners provision the image using either the shell or a configuration management platform.
- Post-processors run after the build to perform tasks with the resulting artifacts.
- Communicators determine how Packer talks to the machine during image creation.
- A build is the overall combination of configurations that result in an image.
- An artifact is the result of a build.
