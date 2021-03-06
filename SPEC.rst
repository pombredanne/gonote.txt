note.txt specification
======================

Motivation
----------

Though it might seem surprising, some believe that the abstraction of the
file, directory and links between them is enough to provide a basic
database structure for storing notes in a unix-y way. This project
**shall** be the empiric proof.

Structure
---------

A note is a simple text file. The first line of this file has to contain
the title of the note. The note itself can be written in any format. The
note file can have any file extension.

The information about the note's creation and last modification time are
stored in its inode record. It is necessary for this data to be easily
retrievable by common tools.

Notes are stored in a central directory. Inside this directory there are
directories which further specify tags attached to a given note. By
default, the notes are tagged with their creation date. To make sure that
they can be easily sorted by running a common directory listing command,
the names of this directories are created in a pattern of YYYY-MM-DD where
YYYY specifies the year, MM the month and DD the day.

In order to add a note into a different tag/directory one can just
create a symbolic link.


File format
-----------

The note file might be of any text based format. Its name **should** be
valid in given filesystem and thus **should** consist of [_a-zA-Z0-9\.-]
which **should** be sufficient for most note titles.

Thus, these files might contan notes:

    some-file-without-extension
    some_file_without_extension
    some-file1.txt
    some....other.file.txt

whereas these might not:

    af425-1.q@22@#%^^&**@! 
    I-do-not-like-you!.txt

The first line of the note file **must** include the title of the note.
