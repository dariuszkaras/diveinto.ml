## Welcome to diveinto.ml

I will make notes about my journey into ML world.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

## tests 

# test for python code 
```python
"""README, Author - Jigyasa Gandhi(mailto:jigsgandhi97@gmail.com)
Requirements:
  - scikit-fuzzy
  - numpy
  - matplotlib
Python:
  - 3.5
"""
import numpy as np
import skfuzzy as fuzz


if __name__ == "__main__":
    # Create universe of discourse in Python using linspace ()
    X = np.linspace(start=0, stop=75, num=75, endpoint=True, retstep=False)

    # Create two fuzzy sets by defining any membership function (trapmf(), gbellmf(),gaussmf(), etc).
    abc1 = [0, 25, 50]
    abc2 = [25, 50, 75]
    young = fuzz.membership.trimf(X, abc1)
    middle_aged = fuzz.membership.trimf(X, abc2)

    # Compute the different operations using inbuilt functions.
    one = np.ones(75)
    zero = np.zeros((75,))
    # 1. Union = max(µA(x), µB(x))
    union = fuzz.fuzzy_or(X, young, X, middle_aged)[1]
    # 2. Intersection = min(µA(x), µB(x))
    intersection = fuzz.fuzzy_and(X, young, X, middle_aged)[1]
    # 3. Complement (A) = (1- min(µA(x))
    complement_a = fuzz.fuzzy_not(young)
    # 4. Difference (A/B) = min(µA(x),(1- µB(x)))
    difference = fuzz.fuzzy_and(X, young, X, fuzz.fuzzy_not(middle_aged)[1])[1]
    # 5. Algebraic Sum = [µA(x) + µB(x) – (µA(x) * µB(x))]
    alg_sum = young + middle_aged - (young * middle_aged)
    # 6. Algebraic Product = (µA(x) * µB(x))
    alg_product = young * middle_aged
    # 7. Bounded Sum = min[1,(µA(x), µB(x))]
    bdd_sum = fuzz.fuzzy_and(X, one, X, young + middle_aged)[1]
    # 8. Bounded difference = min[0,(µA(x), µB(x))]
    bdd_difference = fuzz.fuzzy_or(X, zero, X, young - middle_aged)[1]
```
# test markdown text 
```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
