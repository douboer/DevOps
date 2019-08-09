
## markdown reference
 * [markdown lab](mdlab.md)
 * [asciiflow](http://asciiflow.com/)
 * [markdown参考](https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown#4-%E6%B3%A8%E8%84%)
 * [github emoji](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md#people)
 * [github md](https://help.github.com/en/articles/basic-writing-and-formatting-syntax#using-emoji)



``` graphA → BA → CC → DB → EB → F```

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
?```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
?```


- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item


* Item 1
* Item 2
  * Item 2a
  * Item 2b


1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b


*This text will be italic*
_This will also be italic_
**This text will be bold**
__This will also be bold__
_You **can** combine them_


# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag


#1
mojombo#1
mojombo/github-flavored-markdown#1


```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```
