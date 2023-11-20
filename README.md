# Test

**Part 1 – Mathematics and Logic**

1 - A group of friends at a party drink soda or beer. Thirteen friends drink soda, ten drink beer, and five drink soda and beer. How many friends are present at the party? 

Answer:

- *A* be the set of friends who drink soda,
- *B* be the set of friends who drink beer.

The total number of friends at the party (*A*∪*B*) is given by:

*A*∪*B* =*A*+*B* − *A*∩*B*

Given:

- *A*=13 (friends who drink soda),
- *B*=10 (friends who drink beer),
- *A*∩*B*=5 (friends who drink both soda and beer).

Substitute these values into the formula:

*A*∪*B*=13+10−5

*A*∪*B*=23−5

*A*∪*B*=18

So, there are 18 friends present at the party.

2 - Sarah assumes her watch is 5 minutes late, but it is actually 10 minutes early. Sarah arrives for an appointment thinking she is 15 minutes late compared to the scheduled time. When did she actually arrive? On time, late or early? In case she arrived early, by how many minutes?
Answer:

1. Sarah assumes her watch is 5 minutes late.
2. In reality, the watch is 10 minutes early.

When Sarah arrives for an appointment, she thinks she is 15 minutes late compared to the scheduled time.

The difference between Sarah's perception and the actual time is given by:

Difference=(Assumed delay)+(Actual early)

Difference=(5)+(−10)

Difference=−5

Therefore, the difference is -5 minutes. This means that Sarah actually arrived 5 minutes before the scheduled time. So, she arrived early, and the difference is 5 minutes.

3 - A pizzeria carries out a promotion with the ad "Buy one and get another one for half the price". A different promotion that offers the same discount percentage is: 

Answer:

(d)

4 - Lorenna's phone number has 8 digits, but Sarah only remembers the first four in the correct order. Although she remembers the last four digits and knows that none of them repeats, she has forgotten their order. What's the number of attempts Sarah can make before she can get Lorenna's phone number right?

Answer:

Since Lorenna's phone number has 8 digits and Sarah remembers the first four digits in the correct order, Sarah only needs to guess the order of the last four digits. Sarah knows that none of the last four digits repeats.

The number of ways to arrange the last four digits without repetition is 4!.

4!=4×3×2×1=24.

So, Sarah has 24 possible ways to arrange the last four digits. Therefore, she has 24 attempts to get Lorenna's phone number right.

**Part 2 - Programming**

**1 –** A palindrome is a word that is symmetric: if we write it backward, the result word is the
same. For example, “HANNAH” is a palindrome, but “GAGA” is not. Write a short program
(without using any in-built function) that determines whether a word is a palindrome.

Answer:

```csharp
using System;

class Program
{
    static bool IsPalindrome(string word)
    {
        // Convert the word to uppercase for case-insensitive comparison
        word = word.ToUpper();

        // Get the length of the word
        int length = word.Length;

        // Check if the word is a palindrome
        for (int i = 0; i < length / 2; i++)
        {
            if (word[i] != word[length - i - 1])
            {
                return false;
            }
        }
        return true;
    }

    static void Main()
    {
        Console.Write("Enter a word: ");
        string inputWord = Console.ReadLine();

        if (IsPalindrome(inputWord))
        {
            Console.WriteLine($"{inputWord} is a palindrome.");
        }
        else
        {
            Console.WriteLine($"{inputWord} is not a palindrome.");
        }
    }
}
```

**2 –** A huge phone book containing pairs of the form {phone number, person's name} was
stored as a vector sorted by name in alphabetical order. Write a program (without using any
in-built function) that finds the phone number of a given person in this list, bearing in mind
that the list is very large and that users need the search results to be as fast as possible.

Answer:

```csharp
using System;

class Program
{
    // Data structure to store phone book entries
    struct PhoneBookEntry
    {
        public string Name;
        public string PhoneNumber;
    }

    // Function to perform binary search
    static string FindPhoneNumber(PhoneBookEntry[] phoneBook, string targetName)
    {
        int low = 0;
        int high = phoneBook.Length - 1;

        while (low <= high)
        {
            int mid = (low + high) / 2;
            int comparisonResult = string.Compare(phoneBook[mid].Name, targetName);

            if (comparisonResult == 0)
            {
                // Name found, return the corresponding phone number
                return phoneBook[mid].PhoneNumber;
            }
            else if (comparisonResult < 0)
            {
                // If targetName is greater, search in the right half
                low = mid + 1;
            }
            else
            {
                // If targetName is smaller, search in the left half
                high = mid - 1;
            }
        }

        // Name not found
        return "Phone number not found";
    }

    static void Main()
    {
        // Example phone book data (assuming it's sorted by name)
        var phoneBook = {
            new PhoneBookEntry { Name = "Alice", PhoneNumber = "123-456-7890" },
            new PhoneBookEntry { Name = "Bob", PhoneNumber = "234-567-8901" },
            new PhoneBookEntry { Name = "Charlie", PhoneNumber = "345-678-9012" },
            // ... add more entries as needed
        };

        // Example usage
        Console.Write("Enter the name to find the phone number: ");
        string targetName = Console.ReadLine();

        string phoneNumber = FindPhoneNumber(phoneBook, targetName);

        Console.WriteLine($"Phone number for {targetName}: {phoneNumber}");
    }
}
```

**3 –** Consider the following database schema:

TABLE COLUMNS
------------------ ------------------------------- -----------------------------

SUPPLIER SUPPLIER_CODE, SUPPLIER_NAME, CITY
PART PART_CODE, NAME_PART, PRICE
CAR CAR_CODE, NAME_CAR, TYPE
SUPPLY SUPPLIER_CODE, PART_CODE, CAR_CODE

Write an SQL command that is able to query the suppliers located in the city named
“VITORIA” that provide the part named “MOTOR” for the car named “KOMBI”, with
their respective prices.

Example:
SUPPLIER PRICE

- --------------- ---------
Supplier A 1,000
Supplier B 1,500

Answer:

```sql
SELECT
    S.SUPPLIER_NAME AS SUPPLIER,
    P.PRICE
FROM
    SUPPLIER S
JOIN
    SUPPLY SP ON S.SUPPLIER_CODE = SP.SUPPLIER_CODE
JOIN
    PART P ON SP.PART_CODE = P.PART_CODE
JOIN
    CAR C ON SP.CAR_CODE = C.CAR_CODE
WHERE
    S.CITY = 'VITORIA'
    AND P.NAME_PART = 'MOTOR'
    AND C.NAME_CAR = 'KOMBI';
```

4 - Your friend is developing a small image processing program and has asked for your help
in implementing MS-Paint's “paint bucket”-like functionality. Their program represents
images using arrays of characters, with each array value representing a pixel and letters and
symbols representing different colors. For example, the following 4x6 matrix represents the
letter P in color "#", with background color "." (dot)

```
 .###..
 .#..#.
 .###..
 .#....

```

Your subroutine should take a pixel and a new color and paint the region of that pixel with
the new color, like MS-Paint's “paint bucket” tool.

Examples:

| Pixel (0,1) and new color 'O' | Pixel (1,3) and new color 'o' Pixel (1,3) and new color '#' |
| --- | --- |

| Before

.###..
.#..#.
.###..
.#.... | After

.OOO..
.O..#.
.OOO..

.O.... | .###.
.###..

.#..#.
.#oo#.

Before After Before

.###..

.###.

.#..#.
.###.. | After

.###..
.####.
.###..
.#.... |
| --- | --- | --- | --- |

|  |  | .#....
.#....

.###..

.#.... |  |
| --- | --- | --- | --- |

Answer:

```jsx
function paintBucket(image, x, y, newColor) {
    const oldColor = image[x][y];
    if (oldColor === newColor) {
        return;
    }

    function fill(x, y) {
        if (
            x < 0 || x >= image.length ||
            y < 0 || y >= image[0].length ||
            image[x][y] !== oldColor
        ) {
            return;
        }

        image[x][y] = newColor;

        fill(x + 1, y);
        fill(x - 1, y);
        fill(x, y + 1);
        fill(x, y - 1);
    }

    fill(x, y);
}

// Example usage:
const image = [
    ['.', '#', '#', '#', '.', '.'],
    ['.', '#', '.', '.', '#', '.'],
    ['.', '#', '#', '#', '.', '.'],
    ['.', '#', '.', '.', '.', '.']
];

// Example usage of the paintBucket function
paintBucket(image, 0, 1, 'O');
paintBucket(image, 1, 3, 'o');
paintBucket(image, 1, 3, '#');

// Display the image before and after painting
console.log('Before:');
displayImage(image);

console.log('\nAfter:');
displayImage(image);

function displayImage(image) {
    for (const row of image) {
        console.log(row.join(''));
    }
}
```