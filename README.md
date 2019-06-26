**Swipe\_implementation\_1**

 gesture \_data contain information of information of input file.

 gesture \_info is extracted from gesture\_data.

 expected \_word  is extracted from gesture\_data

 Touch\_point is also extracted from gesture\_data it contain information of the

 trajectory.

 Follow by user

**Get\_suggestion** :-

 get \_suggestion take path as input and find closest character sequence.

How does it do that..

Basically it traverse all the keyboard coordinate for single path coordinate and the nearest one counts. This process is done for every path coordinate.

Now we have a new have path coordinate now we have to find character sequence.

 We already mapped character vs coordinate we simply found the character sequence for new path.

Declare a vector which contain string (suggestion).

First this container contain all the word of dictionary which first and last character match with first and last character of character sequence respectively.

             Now we have to do some elimination.

We let those words in the container whose first and last character is same as character sequence as well as this word present as subsequence.

Our container size reduces after this operation.

           Now final and last thing(last but not least)

 Let me start by  giving you an example qwedfgnm. When we swipe this word you can see that q, w, e are from first row. d, f, g are from second row and n, m from third row, we have to find a new sequence whose consecutive alphabets will not be the same.

We define an integer type variable min\_length this will be equal to the above string length.

We let those words in the container whose size is greater than min\_length-3 and also follow above condition. And this find container will be output. This will contain the list of suggestion.

**Definition of the variable** \_\_

KEY\_LYAOUT:-  contain information of keyboard .precisely which character in which row.

WORDS:- contain all  Dictionary words.

**Definition of functions\_\_**

\_get\_keyboard\_row(char chr): char is in which row

\_match(string path, string word): word is a subsequence of path

\_compress(string sequence): ex-11123311=\&gt;1231

\_get\_minimum\_word\_length(string compress\_str) :return compress\_str.size

\_get\_closest\_char(pair\&lt;int,int\&gt; coordinate)nearest character to this chr

\_get\_closest\_chars\_sequence(vector\&lt;pair\&lt;int,int\&gt;\&gt; path\_cordinate) return

Nearest character to every coordinate of the vector.