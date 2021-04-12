---
layout: default
show_navigation: false
---
https://www.markdownguide.org/basic-syntax/

# Basic syntax

# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6

Heading level 1
===============

Heading level 2
---------------


I really like using Markdown.

I think I'll use it to format all of my documents from now on. 


This is the first line.  
And this is the second line. 


First line with two spaces after.  
And the next line.

First line with the HTML tag after.<br>
And the next line.



I just love **bold text**.  
Love**is**bold 


Italicized text is the *cat's meow*.  
A*cat*meow 


This text is ***really important***.  
This is really***very***important text. <!-- problem  -->


> Dorothy followed her through many of the beautiful rooms in her castle.


> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.


> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.



> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.



1. First item
2. Second item
3. Third item
    1. Indented item
    2. Indented item
4. Fourth item 


- First item
- Second item
- Third item
    - Indented item
    - Indented item
- Fourth item 



1.  Open the file.
2.  Find the following code block on line 21:

        <html>
          <head>
            <title>Test</title>
          </head>

3.  Update the title to match the name of your website.


---


My favorite search engine is [Duck Duck Go](https://duckduckgo.com).

My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").


<https://www.markdownguide.org>  
<fake@example.com>


I love supporting the **[EFF](https://eff.org)**.  
This is the *[Markdown Guide](https://www.markdownguide.org)*.  
See the section on [`code`](#code).

<!-- start problem  -->
In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"
<!-- end problem  -->


[link](https://www.example.com/my%20great%20page)

<!-- start problem  -->
![Tux, the Linux mascot](/assets/images/bossRush.jpg)

[![An old rock in the desert](/assets/images/bossRush.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)
<!-- end problem  -->



\* Without the backslash, this would be a bullet in an unordered list.


This **word** is bold. This <em>word</em> is italic.

---

https://www.markdownguide.org/extended-syntax/

# Extended Syntax

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |


| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |


```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```


Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.


### My Great Heading {#custom-id}

[Heading IDs](#heading-ids)


First Term
: This is the definition of the first term.

Second Term
: This is one definition of the second term.
: This is another definition of the second term.


~~The world is flat.~~ We now know that the world is round.


- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media


😄😸❤️


Gone camping! :tent: Be back soon.

That is so funny! :joy:


http://www.example.com


`http://www.example.com`