# Trie (Prefix Tree)

## **Application**

1. Checking if the prefix/word exists in the dictionary
2. Perform DFS on the trie
3. Used to optimize other algorithms (like DP) to check the prefix/word quickly



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

