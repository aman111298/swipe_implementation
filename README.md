           ** Swype\_implementation\_3 **

 gesture \_data contain information of input file.

 gesture \_info is extracted from gesture\_data.

 expected \_word  is extracted from gesture\_data

 Touch\_point is also extracted from gesture\_data it contains information of the

 trajectory.   Follow by user

 The whole problem runs around the proximity of character so we upload proximity\_file

Proximity file contain information

**&quot;locale&quot;** : **&quot;en\_US&quot;** ,

**&quot;keyboardMinWidth&quot;** : 1080,

**&quot;keyboardHeight&quot;** : 667,

**&quot;gridWidth&quot;** : 32,

**&quot;gridHeight&quot;** : 16,

**&quot;mostCommonKeyWidth&quot;** : 108,

**&quot;mostCommonKeyHeight&quot;** : 165,

**&quot;keyCount&quot;** : 29,

**&quot;proximityCharsArray=[...]**

  **What is proximity mean .**.

 The simple meaning of proximity is nearer adjacent char like for s:-[w, a, z, x, d, e]

**.Get\_suggestion**

    **Proximity\_info**

   For getting information of proximity info \_parse\_proximity() function is called

   This function divide into proximitycharsarray into ...size(proximitycharsarray)/16 blocks.

   Every block is mapped to coordinate that mean whenever you need ...proximity of any character you just have to find a pair of numbers using ..proximity\_box\_coordinate

  you Can find proximity character\_array then filter this proximity   ..character\_array

 (Filter mean remove the negative number and change numerical values into    .charters)

..For given path coordinate for every coordinate find proximity array

  Path\_proximity\_character

  **for** p **in** path\_coordinates:

  proximity\_box\_coordinate = self.\_get\_closest\_proximity\_box(p)

proximity\_characters = self.proximity\_info.get(proximity\_box\_coordinate, [])

proximity\_characters = filter( **lambda** x: x \&gt; ord( **&quot;a&quot;** ), proximity\_characters)

proximity\_characters = tuple(map( **lambda** x: chr(x), proximity\_characters))

path\_proximity\_chars.append(proximity\_characters)

:- chr() convert an integer into character

:- ord() convert character into an integer

:- \_get\_closest\_proximity\_box(){

        **def** \_get\_closest\_proximity\_box(self, p):

        proximity\_box\_width = self.keyboard\_display\_width // self.grid\_n\_cols

        proximity\_box\_height = self.keyboard\_display\_height //self.grid\_n\_row

    **return** Point(p.x // proximity\_box\_width, p.y // proximity\_box\_height)

}

**                                    TO FIND THE FINAL WORD**

**     ** (Complexity will be high because of every possible combination)

**def** \_get\_universal\_word\_set\_itertools(unique\_proximity\_chars):

It does

_#__\*_ _Now out of all the unique character pairs:_

_# \* First we try to get all the possible pairs with length in range [2, n]_

_# \*__Then we get the dense mesh network between formed pairs of various lengths._

_universal\_possible\_words =_ _set__()_

**for** _i_ **in** _xrange__(__2 __,_ _len__ (unique\_proximity\_chars) +_ _1__):_

_   proximity\_chars\_list = itertools.combinations(unique\_proximity\_chars, i)_

_   _ **for** _proximity\_char\_group_ **in** _proximity\_chars\_list:_

_       probable\_words = itertools.product(\*proximity\_char\_group)_

_       _ **for** _word\_chars_ **in** _probable\_words:_

_           universal\_possible\_words.update(_ **&quot;&quot;** _.join(word\_chars))_

**print** _len__(universal\_possible\_words)_

_                       _ **COMBINATION**

_combinations(iterable, r) --\&gt; combinations object_

_Return successive r-length combinations of elements in the iterable._

_combinations(range(4), 3) --\&gt; (0,1,2), (0,1,3), (0,2,3), (1,2,3)_

_     _

_                                 _ **PRODUCT**

_product(\*iterables) --\&gt; product object_

_Cartesian product of input iterables.  Equivalent to nested for-loops._

_For example, product(A, B) returns the same as:  ((x,y) for x in A for y in B)._

_The leftmost iterators are in the outermost for-loop, so the output tuples_

_cycle in a manner similar to an odometer (with the rightmost element changing_

_on every iteration)._

_To compute the product of an iterable with itself, specify the number_

_of repetitions with the optional repeat keyword argument. For example,_

_product(A, repeat=4) means the same as product(A, A, A, A)._

_product(&#39;ab&#39;, range(3)) --\&gt; (&#39;a&#39;,0) (&#39;a&#39;,1) (&#39;a&#39;,2) (&#39;b&#39;,0) (&#39;b&#39;,1) (&#39;b&#39;,2)_

_product((0,1), (0,1), (0,1)) --\&gt; (0,0,0) (0,0,1) (0,1,0) (0,1,1) (1,0,0) ..._
