# Assignment-1 Done by Sachin Gupta and Rahul Sharma
In below code we import two python libraries, one is "random" and "matplotlib".

>First 'Random' library defines a series of functions for generating or manipulating random integers. Python random() is a pseudo-random number generator function that generates a random float number between 0.0 and 1.0, is used by functions in the random module.


>Second 'Matplotlib' library is a comprehensive library for creating static, animated, and interactive visualizations in Python. Matplotlib makes easy things easy and hard things possible. Create publication quality plots.

---

import random
import matplotlib.pyplot as plt
---
The next code cell created a mapping dictionary (mapping_dict) that maps integers from 0 to 9 to their corresponding ASCII values for digits '0' to '9'. The loop then converts each value in the dictionary from ASCII to its corresponding character using the chr() function.
---
mapping_dict=dict(zip(range(0,10),range(48,58)))
for k in mapping_dict.keys():
  mapping_dict[k]=chr(mapping_dict[k])
---
  IN this following cell extending your mapping_dict to include mappings for integers from 10 to 35 to their corresponding uppercase ASCII letters (A to Z).
---
  mapping_dict
for i in range(0,26):
  mapping_dict[10+i]=chr(65+i)

  ---

* Now, the following code tells us about **generating 1000 random numbers and finding the highest base frequency among the 1000 generated numbers and calculating and plotting its relative frequency graph with the help of matplotlib library.**

---


* Here we are ,initializing a variable **sample_size** with the value 1000, and **creating an empty list random_numbers** to store the generated random strings
*  Using a for loop to iterate sample_size times.
*  Creating an empty string blank_str for each iteration to store the
   characters generated in the loop.
* Generating a random integer between 0 and 35 (inclusive) and using it to retrieve a character from mapping_dict, then appending that character to blank_str.


---


sample_size=1000
random_numbers=list()
for i in range(0,sample_size):
  blank_str=str()
  random_digit=random.randint(0,35)
  blank_str=blank_str+mapping_dict[random_digit]
  random_digit=random.randint(0,35)
  blank_str=blank_str+mapping_dict[random_digit]

  for i in range(0,8):
    coin_toss=random.randint(0,1)
    if coin_toss==1:
      random_digit=random.randint(0,35)
      blank_str=blank_str+mapping_dict[random_digit]
    else:
      break
  random_numbers.append(blank_str)

 --- 

*   NOW, creating a **reverse mapping dictionary **(reverse_mapping_dict) where the keys are the characters from mapping_dict, and the values are the corresponding integers.

---
reverse_mapping_dict=dict()
for k in mapping_dict.keys():
  reverse_mapping_dict[mapping_dict[k]]=k


 ---- 

> **Creating a base_frequency dictionary to count the frequency of the highest base in each blank_str from the random_numbers list.**



*   Initializing an empty dictionary called base_frequency to store the frequency of the highest base.


* Now, iterating over each string (blank_str) in the random_numbers list. For each string, you find the highest character (digit) in the string using max(blank_str).

*   Then, you use the reverse_mapping_dict to find the corresponding integer value (reverse_mapping_dict[highest_digit]) and add 1 to it (+1). This gives you the highest base.
---
* Now we are checking if highest_base is already a key in the base_frequency dictionary. If it is, you increment the corresponding value by 1. If not, you create a new entry in the dictionary with the key highest_base and set its value to 1.


---


base_frequency=dict()
for blank_str in random_numbers:
  highest_digit=max(blank_str)
  highest_base=reverse_mapping_dict[highest_digit]+1

  if highest_base in base_frequency.keys():
    base_frequency[highest_base]+=1
  else:
    base_frequency[highest_base]=1

    The following code plot the graph of random numbers with their frequency values.
plt.bar(x=base_frequency.keys(),height=base_frequency.values())
