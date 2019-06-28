**Swipe\_implementation\_5**

The way we traverse

0. Input

1.build\_dict\_trie

2.get\_closestchar\_sequence(0)

3.get commulative\_point(0)

4.get\_proximity\_char(3)

5.get\_break\_point

Creating a objects of suggestore and initialize it by passing file path

File path

(1)  assets/en.xml

(2)  kbd\_layout\_dumper/bobble\_keybord.json

(3) assets/proximity/en/en\_US\_113.json

Set the size of keyboard (1080,585)

**Variable info\_gesture**

It contains opponent path trajectory

**Variable**

Keyboard\_keys\_coordinate\_mapping

Contain information A[(x,y)]=char;

Keyboard\_char\_coordinate\_mapping

Contain information B[char]=(x,y)

**Proximity\_info:-**

Proximity character array divided into block of 16 element size

Information stores in the way

For row in range(row\_size)

For col in range (col\_size)

proximity\_info[row][col]=[.....16 element]

To access the proximity array of any character you have to find corresponding

Row and column.

**Dict trie:-**

We trie is created using all words and whenever a word is completed frequency of corresponding word is given to the node otherwise -1 is given to that node.

**One node has information**

1.Score

2.Character

3.Compound\_character

4.Children

5.Weight

6.dict\_tri\_ref



**get\_suggetion(path\_coordinate)**

Path:- coordinate contain distinct characters that comes along the way

Example {o, p, k, j}



**Comulative\_discreat\_swype\_coordinate**

we know that so many coordinate denote same characters

Example {546,547},{546,547},{540,549}

These coordinate denote same character so we take average of the coordinate and append into list. so final coordinate is {544,548}

**path\_proximity \_char**

It final form will be like

[(i,o,k),(o,l),(i,p,k)]

It contains proximity characters list for every character that comes along the way in the path

**Path\_break\_point**

Form [true,true,false,false…]

**Path\_break\_weight**

Form[5, 2, 2, 0, 2, 2, 0, 5]

Process:-

Find the inflexion of every coordinate in the path

**Inflexion**

i is the current position

pre= path[max(0,i-5):5]

cur= path[i]

next= path[i+1:min(i+5,len(path))]

mean\_preceding\_point= average(pre)

Mean\_succceessive\_point= average(next)

mean\_preceding\_angle= slope(current\_point,preceding\_mean\_point)

mean\_succeeding\_angle= slope(current\_point,succesive\_mean\_point)

delta= abs(mean\_succeeding-mean\_preceding)

If delta is greater than 180 then delta change into 360-delta

Delta is append in inflexion arr

**To find break point**

{(x1,y1),(x2,y2),(x3,y3)-\&gt;(a)}

{in\_ang1,in\_ang2,in\_ang3}

If in\_ang1\&lt;160 then it is breaking point else it is not

Breaking point for above list {1,0,1}

But we needs average of {1,0,1} if average is \&gt; 0.8 then coordinate is break point

NOTE:- first and last coordinate alwage

We will give 5 unit weight to starting and end coording as breaking point weight. Otherwise 2 for breaking point and 0 for not breaking point

weight formate will be [5, 2, 0, 2, 0, 5];

**Proximity\_weight**

Input file for this function:-

1. Path\_characters
2. Path\_break\_point\_weights
3. path\_proximity\_characters,
4. cumulative\_swype\_coordinates

For path a,b,c, proximity characters

a-\&gt;{s,w,q,z}

b-\&gt;{g,v,h,n}

c-\&gt;{x,d,f,v}

After that find maximum distance of every character of proximity of path

\_character



**build\_swype\_trie\_wrt\_dict\_trie**

trie = TrieUtils.build\_swype\_trie\_wrt\_dict\_trie(path, path\_proximity\_chars, proximity\_weights,path\_break\_points, self.dict\_trie)

All input file already discussed

root = Node()

level\_to\_node\_mapping = {0: [root]}

**#What is the root?**

It is a starting point of trie, and we start our traversal from the root

**break\_point\_pairs** TrieUtils.\_get\_break\_point\_start\_end\_pairs(swype\_path\_is\_break\_pt)

Example:-  for break point {1,0,1,0,1,0,1},break\_point\_pairs [(1,3),(3,5),(5,7)]

Now we traverse in dict tree and form a new try for given input and

Finally traverse the build tree and where value is zero we return compound with score.