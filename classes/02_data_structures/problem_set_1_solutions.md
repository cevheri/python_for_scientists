# Data Structures - Solutions

## Lists

#### 1. Initialize a list called "boys" with the elements: "Fred", "George", "Percy", "Ron".

    boys = ["Fred", "George", "Percy", "Ron"]
    
#### 2. Initialize a list called "girls" with elements: "Giney".

    girls = ["Giney"]
    
#### 3. Print both lists.

    print(boys)
    print(girls)
    
#### 4. Print the first element in "girls".

    girls[0]
    
#### 5. Find two or three ways to print the last element in "boys".

    boys[3]
    boys[len(boys) - 1]
    boys[-1]
    
#### 6. Add the element "Charles" to the "boys" list.

    boys.append("Charles")

#### 7. Add the "boys" and "girls" together, and save the results as a list called "weasleys".
    
    weasleys = boys + girls
    
#### 8. Use the `.sort()` method to sort the "weasleys" list into alphabetical order.
    
    weasleys.sort()
    print(weasleys)
    
#### 9. Print the length of `weasleys`.

    print(len(weasleys))
    
#### 10. Using a `for` loop, iterate through `weasleys` and add the first letter of each name to into a string called "firsts", then print that string.

    firsts = ''
    for name in weasleys:
        firsts += name[0]
    
    print(firsts)
    
#### 11. Using a `for` loop and an `if` statement, iterate through `weasleys` and create a new list, "reds", of only names longer than 4 letters.

    reds = []
    for name in weasleys:
        if len(name) > 4:
            reds.append(name)
    
    print(name)
    
#### 12. Using an `in` statement, test if "Charles" is in the `weasleys`.

    "Charles" in weasleys
    
#### 13. Using a slice (`[:]`), take a slice of all but the first and last elements of `weasleys`.

    weasleys[1:-1]
    
#### 14. Using two slices (`[:]`), add the first element of `boys` to the last element of `weasleys`.

    boys[0] + weasleys[-1]

## Dictionaries

#### 1. Create an empty dictionary named "tardis".

    tardis = {}
    
#### 2. Add a key/value pair to tardis of "Doctor"/"Who".

    tardis['Doctor'] = 'Who'
    
#### 3. Add a key/value pair to the tardis dictionary of "Dalek"/"Evil".

    tardis['Dalek'] = 'Evil'
    
#### 4. Print the tardis dictionary. Print the keys. Print the values.

    tardis
    tardis.keys()
    tardis.values()
    
#### 5. Change the value of "Dalek" to "Exterminate"

    tardis["Dalek"] = "Exterminate"

#### 6. Add the key/value pair "Companion"/"Human" to `tardis`.
    
    tardis["Companion"] = "Human"
    
#### 7. Print tardis (in two different ways).

    tardis
    print(tardis)

#### 8. Using a `for` loop and `.keys()`, print the values of the `tardis`.

    tardis_keys = tardis.keys()
    for key in tardis_keys:
        print(tardis[key])

#### 9. Without using `.keys()` or `.values()`, use a `for` loop to print the values of the `tardis`.

    for name in tardis:
        print(tardis[name])

#### 10. Save the Doctor! Remove the "Dalek" key from the dictonary.

    del tardis["Dalek"]
    
#### 11. Print tardis.

    tardis

#### 12. Find the number of keys in the `tardis`.

    # version 1 - Best Option
    len(tardis)
    
    # version 2
    len(tardis.keys())

#### 13. Using `sorted` and a slice (`[:]`), print the `keys` of `tardis` in reverse alphabetical order.

    sorted(tardis.keys())[::-1]

## Tuples

#### 1. Create a tuple called "months" containing the words "January" and "February".

    months = ("January", "February")
    
#### 2. Add "March" to the "months" tuple.

    # TRICK QUESTION: You can't modify a tuple.
    
#### 3. Change "January" to "June".

    # TRICK QUESTION: You can't modify a tuple.
    
#### 4. Return the first element in "months"

    months[0]
    
#### 5. Return the last element in "months" in two or three different ways.

    months[-1]
    months[1]
    months[len(months) - 1]

## Sets

#### 1. Create a empty sets called "insects".

    insects = set()
    
#### 2. One-at-a-time, add these elements to insects: "6 legs", "exoskeleton", "3-part bodies", "small", "lay eggs"

    insects.add("6 legs")
    insects.add("exoskeleton")
    insects.add("3-part bodies")
    insects.add("small")
    insects.add("lay eggs")
    
#### 3. Create a new set called "spiders" that starts off including the elements: "8 legs", "spin webs", "2-part bodies", "small", "lay eggs"

    spiders = set(["8 legs", "spin webs", "2-part bodies", "small", "lay eggs"])
    
#### 4. Print both sets.

    >>> insects
    >>> spiders
    
#### 5. Find the intersection of both sets.

    >>> insects.intersection(spiders)
    set(["small", "lay eggs"])
    
#### 6. Determine if either set is a subset of the other.

    >>> insects.issubset(spiders)
    False
    >>> spiders.issubset(insects)
    False
    >>> insects.issuperset(spiders)
    False
    >>> spiders.issuperset(insects)
    False
    
#### 7. Add "not cuddly" to the spider set, and print.

    >>> spiders.add("not cuddly")
    >>> spiders
    set(["8 legs", "spin webs", "2-part bodies", "small", "lay eggs", "not cuddly"])
    
#### 8. Remove the "not cuddly" from the spiders set, and print.

    >>> spiders.remove("not cuddly")
    >>> spiders
    set(["8 legs", "spin webs", "2-part bodies", "small", "lay eggs"])


## Choose a Data Structure

Knowning how to use a particular data structure is good, but that won't do you any good unless you know when to pick various data structures. In the problems below, pick one of the four data structures above to solve the problem as easily as possible.

#### 1. Print the days of the week (`"Monday"` through `"Sunday"`) and the numbers `1` through `7` using a single `for` loop.

    dows = ("Monday", "Tuesday", "Wednesday", "Thursday",
            "Friday", "Saturday", "Sunday")
    
    for i, dow in enumerate(dows):
        print(dow + " is day-of-week number " + str(i))

#### 2. Print the names of the planets in alphabetical order: `"Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"`.

    planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
    
    for planet in sorted(planets):
        print(planet)

#### 3. Create a collection of the names of three science fiction auhors `"Ray Bradbury"`, `"Isaac Asimov"`, and `"Terry Pratchett"` such that it can never be altered.

    authors = ("Ray Bradbury", "Isaac Asimov", "Terry Pratchett")

#### 4. Find all the unique letters in the phrase: `"the sweettoothed bookkeeper"`.

    letters = set("the sweettoothed bookkeeper".replace(' ', ''))

#### 5. For each month of the year, match the number of days in the month to the number (1 through 12) of that month.

Notice I didn't say you needed to do any math. All you need to do is *assign* values. So just create a dictionary.

    months = {1: 31, 2: 28, 3: 31, 4: 30, 5: 31, 6: 30,
              7: 31, 8: 31, 9: 30, 10: 31, 11: 30, 12: 31}


[Back to Problem Set](problem_set_1_data_structures.md)
