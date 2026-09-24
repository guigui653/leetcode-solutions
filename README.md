# LeetCode Solutions - Guilherme's DSA Journey

[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)](.)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](.)
[![LeetCode](https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com)

Repositório com soluções de problemas de **estruturas de dados e algoritmos** resolvidos no LeetCode. Foco em **Java** (para backend/Spring Boot) e **Python** (breadth).

## 🎯 Objetivo

- Dominar conceitos fundamentais de DSA
- Melhorar pensamento algorítmico
- Construir portfólio público de qualidade
- Preparação para entrevistas técnicas

## 📊 Progresso

| Linguagem | Easy | Medium | Hard | Total |
|-----------|------|--------|------|-------|
| Java      | 0    | 0      | 0    | 0     |
| Python    | 0    | 0      | 0    | 0     |
| **Total** | **0**| **0**  | **0**| **0** |

## 🗂️ Organização

```
java/
  ├── easy/      → Problemas nível iniciante
  ├── medium/    → Problemas intermediários (foco principal)
  └── hard/      → Problemas avançados

python/
  ├── easy/
  ├── medium/
  └── hard/

docs/
  ├── java-patterns.md    → Snippets e padrões úteis
  └── python-patterns.md  → Snippets e padrões úteis
```

## 📚 Como Usar Este Repo

Cada solução segue este padrão (exemplo abaixo):

### Exemplo: TwoSum.java

```java
/**
 * Problem: Two Sum
 * Link: https://leetcode.com/problems/two-sum/
 * 
 * Difficulty: Easy
 * Time Complexity: O(n)
 * Space Complexity: O(n)
 * 
 * Approach: Use HashMap para armazenar valores já vistos
 * Insights: Pensamiento em complement - procure pelo número que falta (target - num)
 */

public class TwoSum {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seen = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            
            if (seen.containsKey(complement)) {
                return new int[] { seen.get(complement), i };
            }
            
            seen.put(nums[i], i);
        }
        
        return new int[] {};
    }
}
```

## 🛣️ Roadmap (12 semanas)

Veja [ROADMAP.md](ROADMAP.md) para o plano completo com problemas específicos.

**Resumo das semanas:**
- **Semanas 1-3**: Arrays, Strings, Dois Pointers
- **Semanas 4-6**: Hash Maps, Stacks, Queues
- **Semanas 7-9**: LinkedLists, Trees, Recursão
- **Semanas 10-12**: Graphs, DP, Revisão

## 🔗 Links Úteis

- [LeetCode Profile](https://leetcode.com/guigui653)
- [GitHub Profile](https://github.com/guigui653)
- [LinkedIn](https://linkedin.com/in/seu-linkedin)

---

**Last Updated**: 24 de Setembro de 2026  
**Status**: 🚀 Em Progresso
