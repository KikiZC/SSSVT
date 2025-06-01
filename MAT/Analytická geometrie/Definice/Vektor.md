## Co je vektor?
- Vektor = **veličina s velikostí, směrem a orientací**.
- Ve fyzice znázorňuje např. **sílu**.
- V matematice je vektor:
  - Množina **všech orientovaných úseček** se stejnou délkou, směrem a orientací.

## Orientovaná úsečka
- Úsečka AB:
  - A = **počáteční bod**
  - B = **koncový bod**
- Po prohození bodů (BA) → **opačně orientovaná úsečka**.

## Nulový vektor
- Vektor s **nulovou délkou** a **žádným směrem**.
- Množina všech orientovaných úseček délky 0.

---

## Souřadnice vektoru
- Vektor 
$$\vec{u}$$ 
- daný úsečkou AB:
$$ A = [a_1, a_2], \quad B = [b_1, b_2]$$
- Jeho souřadnice budou potom:
$$
\vec{u} = [b_1 - a_1, b_2 - a_2]
$$

## Posunutí bodu vektorem
Pusunití bodu A o vektor u
$$
A = [a_1, a_2] \quad \vec{u} = (u_1, u_2)
$$
potom
$$
A + \vec{u} = [a_1 + u_1, a_2 + u_2]
$$
Tento vzorec lze použít na více souřadnic. Jen se přidá další kolonka.

---

## Příklady:
1. **Vypočítej souřadnice vektoru**  
Body:  
$$
   A = [1, 3, 7], \quad B = [-1, 1, 2] 
$$
> [!success] Vektor:  
>$$
   \vec{u} = B - A = [-1 - 1, 1 - 3, 2 - 7] = (-2, -2, -5)
$$

2. **Spočítej bod B ze součtu A + u**  
Zadání:
$$
A = [-1, -2, 3], \quad \vec{u} = (3, 1, 1) 
$$
> [!success] Bod B
>$$
B = A + u = [-1 + 3, -2 + 1, 3 + 1] = [2, -1, 4]
$$
---

## Sčítání a odčítání vektorů
- Dva vektory:  
$$
  \vec{u} = (u_1, u_2), \quad \vec{v} = (v_1, v_2)
$$
- Součet:  
$$
  \vec{w} = \vec{u} + \vec{v} = (u_1 + v_1, u_2 + v_2)
$$
- Vlastnosti:
  - Komutativita: 
$$
\vec{u} + \vec{v} = \vec{v} + \vec{u}
$$
  - Asociativita: 
  $$
  (\vec{u} + \vec{v}) + \vec{w} = \vec{u} + (\vec{v} + \vec{w})
$$
  - Distributivita skalárního násobení

- Opačný vektor:  
$$
  -\vec{u} = (-u_1, -u_2)
$$
- Rozdíl vektorů:  
$$
  \vec{u} - \vec{v} = \vec{u} + (-\vec{v})
$$
---

## Násobení vektoru skalárem
$$
\text{Skalár} \quad c \in \mathbb{R}, \quad \text{vektor} \quad \vec{u} = (u_1, u_2)
$$
> [!success] Výsledek:  
> $$
  c \times \vec{u} = (c \times u_1, c \times u_2)
> $$
---

## Lineární kombinace vektorů
$$
\text{Pro} \quad (a, b \in \mathbb{R} ), \vec{u} = (u_1, u_2), \vec{v} = (v_1, v_2)
$$
Platí:
$$
a \times \vec{u} + b \times \vec{v} = (a \times u_1 + b \times v_1,\ a \times u_2 + b \times v_2)
$$
---
##  Lineární závislost

- Vektory:  
  $$
  \vec{u}_1,\ \vec{u}_2,\ \dots,\ \vec{u}_n
  $$

- Pokud existují koeficienty  
  $$
  a_1,\ a_2,\ \dots,\ a_{n-1} \in \mathbb{R}
  $$  
  takové, že platí:

  $$
  \vec{u}_n = a_1\vec{u}_1 + a_2\vec{u}_2 + \dots + a_{n-1}\vec{u}_{n-1}
  $$

  → **vektory jsou lineárně závislé**  
- Jinak → **lineárně nezávislé**

---

## Příklad

Vektory:  
$$
\vec{u} = (3,\ 0,\ -2),\quad \vec{v} = (-4,\ 3,\ 5)
$$

- **Součet:**  
  $$
  \vec{u} + \vec{v} = (3 + (-4),\ 0 + 3,\ -2 + 5) = (-1,\ 3,\ 3)
  $$

- **Rozdíl:**  
  $$
  \vec{u} - \vec{v} = (3 - (-4),\ 0 - 3,\ -2 - 5) = (7,\ -3,\ -7)
  $$

- **Lineární kombinace \( 3\vec{u} - 2\vec{v} \):**

  $$
  \begin{aligned}
  3\vec{u} &= (9,\ 0,\ -6) \\
  2\vec{v} &= (-8,\ 6,\ 10) \\
  3\vec{u} - 2\vec{v} &= (9 - (-8),\ 0 - 6,\ -6 - 10) = (17,\ -6,\ -16)
  \end{aligned}
  $$