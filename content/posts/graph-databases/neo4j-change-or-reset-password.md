+++
title = "How to reset or change the Neo4j graph database password"
authors = ['Rajendra Kadam']
date= 2022-04-27T18:11:54+00:00
lastmod = 2024-02-13T22:28:17+05:30
draft = false
series = ['Neo4j Basics']
categories = ['Neo4j']
tags = ['Neo4j', 'Neo4j Password']
url = "/neo4j/neo4j-change-or-reset-password/"
featuredImage = "/wp-content/uploads/2022/04/Neo4j-password.png"
excerpt = 'Have forgotten your Neo4j database password? Don’t worry, I am sharing two ways to reset or change your Neo4j graph database password.'
summary = 'Have forgotten your Neo4j database password? Don’t worry, I am sharing two ways to reset or change your Neo4j graph database password.'
+++

**Have forgotten your Neo4j database password? Don’t worry, I am sharing two ways to reset or change your Neo4j graph database password.**

In some cases simply deleting the existing neo4j database or neo4j installation and installing it again may work. But it's not an option every time especially when the database already has some data in it. 

## What are the default username and passwords of the Neo4j database? {.wp-block-heading}

If you have recently installed Neo4j and didn't set any password then your database might have the default username and password. You can try the following credentials:

**Username:** _`neo4j`_

**Password:** _`neo4j`_

If it works then great otherwise you can reset your password using one of the following methods.



## Method 1: For Neo4j desktop installation only {.wp-block-heading}

Neo4j desktop has become a very popular option to work with the Neo4j graph database. It provides a beautiful interface and is very easy to install Neo4j and other graph applications. 

<figure class="wp-block-image size-large is-resized is-style-default">

<img loading="lazy" decoding="async" src="/wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-1024x319.png" alt="Neo4j desktop create local database" class="wp-image-57" width="812" height="253" srcset="/wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-1024x319.png 1024w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-300x94.png 300w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-768x240.png 768w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-1536x479.png 1536w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-2048x639.png 2048w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-10.58.09-PM-150x47.png 150w" sizes="(max-width: 812px) 100vw, 812px" /> <figcaption>Neo4j desktop &#8211; create a database screen</figcaption></figure> 

When you create a local database it asks you to enter a password. Most of the time we enter some random password and then don't remember it later whenever we need it for connecting it.

Resetting or changing the Neo4j password through the Neo4j desktop is quite easy. You just need to open the Neo4j desktop. Go to the database screen and click on the database. It will show an additional section on the right side. 

Click on the **Details** tab and then the **Reset DBMS password** option, Here you can set a new password.<figure class="wp-block-image size-large">

<img loading="lazy" decoding="async" width="1024" height="331" src="/wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-1024x331.png" alt="Reset password on Neo4j desktop" class="wp-image-58" srcset="/wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-1024x331.png 1024w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-300x97.png 300w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-768x248.png 768w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-1536x496.png 1536w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-2048x662.png 2048w, /wp-content/uploads/2022/04/Screenshot-2022-04-27-at-11.07.26-PM-150x48.png 150w" sizes="(max-width: 1024px) 100vw, 1024px" /> </figure> 



## Method 2: Neo4j Server Installation (Zip/Tar) {.wp-block-heading}

Unfortunately, In some cases, we don't have an option to install the Neo4j desktop. We need to install it through a zip file(**Windows**) or a tar file(**Linux/Mac**). 

Neo4j stores its auth details in the _`auth.ini`_ file. For obvious security reasons Neo4j stores authentication details in the encrypted format so it's not possible to recover the existing password from this file. The only option we have is to delete this auth file and set the new password when we access the Neo4j after a restart.

<ol>
  <li>
    First, stop the Neo4j database if it's running. Auth file is located inside&nbsp;<strong>“$NEO4J_HOME/data/dbms/”</strong>&nbsp;directory. Navigate to this location.
  </li>
  <li>
    Delete the&nbsp;<strong>auth file</strong>&nbsp;(if you are using Linux and don’t have permission to delete the file. Open the terminal and delete the file using superuser access).
  </li>
  <li>
    <strong>Restart the neo4j server.</strong>
  </li>
  <li>
    Open a neo4j browser, and log in with the default username/password: i.e.&nbsp;<strong>neo4j/neo4j</strong>. It will ask you to set a new password.
  </li>
</ol>

**This method is also applicable to other distributions and other methods of installation like terminal installation (Including the Neo4j desktop database). You can find the location of a data folder(auth.ini) for your distributions&nbsp;[File locations][1].**

 [1]: https://neo4j.com/docs/operations-manual/current/configuration/file-locations/