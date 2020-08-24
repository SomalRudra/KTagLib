# KTagLib

Kotlin bindings for [TagLib](https://github.com/taglib/taglib)


To get a Git project into your build:

Step 1. Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

Step 2. Add the dependency

	dependencies {
	        implementation 'com.github.SomalRudra:KTagLib:1.0'
	}


See the sample app for an example of reading tags, using the Storage Access Framework.


## Usage ##

#### Read Tags ####

Read the tags from a file descriptor:

`KTagLib.getMetadata(fd: Int)`

This returns a HashMap representing the tags (metadata) of the audio file located at `FileDescriptor` fd.

#### Retrieve Artwork ####

`getArtwork(fd: Int)`

Returns a `ByteArray` (or null) representing the image data of the largest image found.

#### Write Tags ####

    fun updateTags(
            fd: Int,
            properties : HashMap<String, String>
        ): Boolean

Attempts to write the tags supplied as a HashMap to the file located at `FileDescriptor` 'fd'.

Note: All tags passed to properties are replaced in the file. Therefore, only pass fields you want to
change. To clear a tag, pass an empty string.

Returns true if the tags are successfully updated.
