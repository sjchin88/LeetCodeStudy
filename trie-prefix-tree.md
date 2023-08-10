# Trie (Prefix Tree)

## **Application**

1. Checking if the prefix/word exists in the dictionary
   1. Fastest in finding common prefix - putting the words into the Trie one by one, and find the max/min common prefix of the new word with the previous word
2. Perform DFS on the trie
   1. When we want to dfs based on the prefix, to check if the prefix can lead to a word will need O(L)
   2. But if we already at the node of previous character in the Trie, to check if the next character can lead to a word will only need O(1) time
3. Used to optimize other algorithms (like DP) to check the prefix/word quickly
   1. When we have a set of words with some common prefix, and we need to dp based on the word and target
   2. Like all words that can be transformed into target with less than or equal to k operation&#x20;



## Things to Note:

1. In normal TrieNode, look to modify the variable to suit the problem (like adding a self.count for all words )

## Algorithm&#x20;

### TrieNode & Trie (Python)

```python

class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_word = False
        self.word = None

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def get_root(self):
        return self.root
        
    def insert(self, word:str):
        node = self.root
        for i in range(len(word)):
            if word[i] not in node.children:
                node.children[word[i]] = TrieNode()
            node = node.children[word[i]]
        node.is_word = True
        node.word = word
```

### TrieNode & Trie (Java)

```java
class TrieNode {
    public Map<Character, TrieNode> children;
    public boolean isWord;
    public String word;
    
    public TrieNode(){
        this.children = new HashMap<>();
        this.isWord = False;
        this.word = null;
    }
}

class Trie{
    private TrieNode root;
    public Trie(){
        this.root = TrieNode();
    }
    
    public TrieNode getRoot(){
        return this.root;
    }
    
    public void insert(String word){
        TrieNode node = this.root;
        for (int i = 0; i < word.length(); i++){
            if (!node.children.containsKey(word.charAt(i)){
                node.children.put(word.charAt(i), new TrieNode());
            }
            node = node.children.get(word.charAt(i));
        }
        node.isWord = True;
        node.word = word;
    }
}
```

## Practise

Lintcode 1624 - common prefix

Lintcode 623 - Use Trie to store common dp result and accelerate DP

Lintcode 1848 - Use Trie to speed up the check for dfs
