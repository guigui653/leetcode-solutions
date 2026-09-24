# 📚 Python Patterns & Snippets

Referência rápida de padrões úteis ao resolver problemas de DSA em Python.

---

## 1️⃣ Dictionary - Frequency Counting

```python
# Contar frequência de elementos
from collections import Counter

freq = Counter(nums)  # Mais pythônico

# Ou manualmente
freq = {}
for num in nums:
    freq[num] = freq.get(num, 0) + 1

# Acessar
count = freq.get(target, 0)

# Iterar
for key, value in freq.items():
    print(key, value)
```

---

## 2️⃣ Set - Contains & Duplicates

```python
# Set para busca O(1)
seen = set()

# Adicionar
seen.add(num)

# Verificar
if num in seen:
    # existe

# Remove
seen.remove(num)  # Raise erro se não existe
seen.discard(num) # Sem erro se não existe
```

---

## 3️⃣ Two Pointers Pattern

```python
# Exemplo: Two Sum Sorted Array
left, right = 0, len(arr) - 1

while left < right:
    current_sum = arr[left] + arr[right]
    
    if current_sum == target:
        return [left, right]
    elif current_sum < target:
        left += 1  # Aumentar soma
    else:
        right -= 1  # Diminuir soma
```

---

## 4️⃣ Sliding Window Pattern

```python
# Exemplo: Longest Substring Without Repeating Characters
def lengthOfLongestSubstring(s):
    left = 0
    max_len = 0
    window = {}  # char -> index
    
    for right in range(len(s)):
        ch = s[right]
        
        # Se duplicado, mover left
        if ch in window and window[ch] >= left:
            left = window[ch] + 1
        
        window[ch] = right
        max_len = max(max_len, right - left + 1)
    
    return max_len
```

---

## 5️⃣ Stack Pattern

```python
# Pilha usando list
stack = []

# Operações
stack.append(value)     # Push
top = stack[-1]         # Peek (sem remover)
popped = stack.pop()    # Pop (com remover)
is_empty = len(stack) == 0

# Exemplo: Valid Parentheses
def isValid(s):
    stack = []
    mapping = {'(': ')', '{': '}', '[': ']'}
    
    for char in s:
        if char in mapping:
            stack.append(char)
        else:
            if not stack or mapping[stack.pop()] != char:
                return False
    
    return len(stack) == 0
```

---

## 6️⃣ Queue Pattern

```python
from collections import deque

queue = deque()

# Operações
queue.append(value)     # Adiciona ao final
front = queue[0]        # Pega do início (sem remover)
removed = queue.popleft() # Remove do início
```

---

## 7️⃣ Sorting

```python
# Listas
nums.sort()                          # In-place, crescente
nums.sort(reverse=True)              # In-place, decrescente
sorted_nums = sorted(nums)           # Novo array, crescente
sorted_nums = sorted(nums, reverse=True)  # Novo array, decrescente

# Sorted com key customizado
people.sort(key=lambda x: x[1])  # Ordenar por 2º elemento

# Por múltiplos critérios
people.sort(key=lambda x: (x[0], -x[1]))  # Primeiro crescente, depois decrescente
```

---

## 8️⃣ String Operations

```python
# Conversão
s = str(123)        # int → string
n = int("123")      # string → int
chars = list(s)     # string → list de chars
s2 = ''.join(chars) # list → string

# Métodos úteis
len(s)
s[index]
s[start:end]        # Slicing
s == other
s.lower()
s.upper()
s.split(',')
',' in s
s.strip()           # Remove espaços
s.replace('a', 'b')
```

---

## 9️⃣ List Comprehension

```python
# Básico
squared = [x**2 for x in nums]

# Com condição
evens = [x for x in nums if x % 2 == 0]

# Nested
matrix = [[i*j for j in range(3)] for i in range(3)]

# Dict comprehension
freq = {char: s.count(char) for char in s}
```

---

## 🔟 LinkedList Definition

```python
# Node
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

# Traversal
current = head
while current:
    # Process current.val
    current = current.next
```

---

## 1️⃣1️⃣ Binary Search

```python
# Em array ordenado
def binarySearch(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1  # Não encontrado
```

---

## 1️⃣2️⃣ TreeNode Definition

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

# DFS - Inorder (Esquerda → Node → Direita)
def inorder(root):
    if not root:
        return
    inorder(root.left)
    print(root.val)
    inorder(root.right)

# BFS - Level Order
from collections import deque

def levelOrder(root):
    if not root:
        return
    
    queue = deque([root])
    
    while queue:
        node = queue.popleft()
        print(node.val)
        
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
```

---

## 1️⃣3️⃣ Defaultdict

```python
from collections import defaultdict

# Evita KeyError
freq = defaultdict(int)
freq[key] += 1

# Ou
graph = defaultdict(list)
graph['A'].append('B')
```

---

## 💡 Tips

- Use `deque` para queues (mais eficiente que list.pop(0))
- Use `Counter` para contar frequências
- Use `defaultdict` para evitar KeyError
- List comprehensions são mais rápidas que loops
- Use slicing `[:]` para copiar listas
- Strings são imutáveis, use list ou StringBuilder

---

**Última atualização**: 24 de Setembro de 2026
