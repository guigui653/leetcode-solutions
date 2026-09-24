# 📚 Java Patterns & Snippets

Referência rápida de padrões úteis ao resolver problemas de DSA em Java.

---

## 1️⃣ HashMap - Frequency Counting

```java
// Contar frequência de elementos
Map<Integer, Integer> freq = new HashMap<>();
for (int num : nums) {
    freq.put(num, freq.getOrDefault(num, 0) + 1);
}

// Acessar
int count = freq.getOrDefault(target, 0);

// Iterar
for (Map.Entry<Integer, Integer> entry : freq.entrySet()) {
    int key = entry.getKey();
    int value = entry.getValue();
}
```

---

## 2️⃣ HashSet - Contains & Duplicates

```java
Set<Integer> seen = new HashSet<>();

// Adicionar
seen.add(num);

// Verificar
if (seen.contains(num)) {
    // existe
}

// Remove
seen.remove(num);
```

---

## 3️⃣ Two Pointers Pattern

```java
// Exemplo: Two Sum Sorted Array
int left = 0, right = arr.length - 1;

while (left < right) {
    int sum = arr[left] + arr[right];
    
    if (sum == target) {
        return new int[] { left, right };
    } else if (sum < target) {
        left++;  // Aumentar soma
    } else {
        right--; // Diminuir soma
    }
}
```

---

## 4️⃣ Sliding Window Pattern

```java
// Exemplo: Longest Substring Without Repeating Characters
int left = 0;
int maxLen = 0;
Map<Character, Integer> window = new HashMap<>();

for (int right = 0; right < s.length(); right++) {
    char ch = s.charAt(right);
    window.put(ch, window.getOrDefault(ch, 0) + 1);
    
    // Encolher janela se duplicate
    while (window.get(ch) > 1) {
        char leftChar = s.charAt(left);
        window.put(leftChar, window.get(leftChar) - 1);
        if (window.get(leftChar) == 0) {
            window.remove(leftChar);
        }
        left++;
    }
    
    maxLen = Math.max(maxLen, right - left + 1);
}
```

---

## 5️⃣ Stack Pattern

```java
Stack<Integer> stack = new Stack<>();

// Operações básicas
stack.push(value);
int top = stack.peek();      // Sem remover
int popped = stack.pop();    // Com remover
boolean empty = stack.isEmpty();

// Exemplo: Valid Parentheses
for (char ch : s.toCharArray()) {
    if (ch == '(') {
        stack.push(ch);
    } else if (ch == ')') {
        if (stack.isEmpty() || stack.pop() != '(') {
            return false;
        }
    }
}
```

---

## 6️⃣ Queue Pattern

```java
Queue<Integer> queue = new LinkedList<>();

// Operações
queue.add(value);           // Adiciona ao final
int front = queue.peek();   // Pega do início (sem remover)
int removed = queue.poll(); // Remove do início
```

---

## 7️⃣ Sorting

```java
// Arrays
Arrays.sort(arr);                           // Crescente
Arrays.sort(arr, Collections.reverseOrder()); // Decrescente (Integer[])

// Listas
Collections.sort(list);                     // Crescente
Collections.sort(list, Collections.reverseOrder()); // Decrescente

// Comparator personalizado
list.sort((a, b) -> Integer.compare(b, a)); // Decrescente
```

---

## 8️⃣ String Operations

```java
// Conversão
String s = String.valueOf(123);       // int → String
int n = Integer.parseInt("123");      // String → int
char[] chars = s.toCharArray();       // String → char[]
String s2 = new String(chars);        // char[] → String

// Métodos úteis
s.length();
s.charAt(index);
s.substring(start, end);
s.equals(other);
s.equalsIgnoreCase(other);
s.split(",");
s.contains("sub");
```

---

## 9️⃣ LinkedList Definition

```java
// Node simplificado (não use em prod, apenas para entender)
public class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
    }
}

// Traversal
ListNode current = head;
while (current != null) {
    // Process current.val
    current = current.next;
}
```

---

## 🔟 Binary Search

```java
// Em array ordenado
int left = 0, right = arr.length - 1;

while (left <= right) {
    int mid = left + (right - left) / 2; // Evita overflow
    
    if (arr[mid] == target) {
        return mid;
    } else if (arr[mid] < target) {
        left = mid + 1;
    } else {
        right = mid - 1;
    }
}

return -1; // Não encontrado
```

---

## 1️⃣1️⃣ TreeNode Definition

```java
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) {
        this.val = val;
    }
}

// DFS - Inorder (Esquerda → Node → Direita)
void inorder(TreeNode root) {
    if (root == null) return;
    inorder(root.left);
    System.out.println(root.val);
    inorder(root.right);
}

// BFS - Level Order
void levelOrder(TreeNode root) {
    Queue<TreeNode> queue = new LinkedList<>();
    queue.add(root);
    
    while (!queue.isEmpty()) {
        TreeNode node = queue.poll();
        System.out.println(node.val);
        
        if (node.left != null) queue.add(node.left);
        if (node.right != null) queue.add(node.right);
    }
}
```

---

## 1️⃣2️⃣ Common Imports

```java
import java.util.*;
import java.util.HashMap;
import java.util.HashSet;
import java.util.Stack;
import java.util.Queue;
import java.util.LinkedList;
import java.util.Arrays;
import java.util.Collections;
```

---

## 💡 Tips

- Use `getOrDefault()` em maps para evitar NullPointerException
- Evite overflow: `mid = left + (right - left) / 2`
- Strings são imutáveis — use StringBuilder para concatenação repetida
- LinkedList é lento para acesso aleatório — use ArrayList para indexação
- Para comparar Strings, use `.equals()` não `==`

---

**Última atualização**: 24 de Setembro de 2026
