# Монадные трансформеры

## Как запустить тесты

```bash
stack test --test-arguments "tier0" # Тесты для задачи на тройку
stack test --test-arguments "tier1" # Тесты для задачи на четвёрку
stack test --test-arguments "tier2" # Тесты для задачи на пятерку
```

## Задача на 3

В файле `src/Tier0/Task.hs` определен тип данных, представляющий [двоичное дерево](https://en.wikipedia.org/wiki/Binary_tree):

```
data Tree a = Leaf a | Branch (Tree a) a (Tree a) deriving Eq
```

1. Реализуйте функцию `sumAndModifyInOrder :: Num a => Tree a -> State [a] a`, которая при участии монады `State`:
   * вычисляет сумму значений в вершинах дерева;
   * выписывает значения в вершинах в порядке [центрированного обхода двоичного дерева](https://en.wikipedia.org/wiki/Tree_traversal#In-order,_LNR).

Например, для дерева `tree`

```
    4
   / \
  2   5
 / \
1   3
```

Вычисление внутри монады `State`

```haskell
runState (sumAndModifyInOrder tree) []
```

должно породить значение `(15, [1,2,3,4,5])`.

2. В файле `src/Tier0/Task.hs` также определён вспомогательный тип данных, комбинирующий монады `Maybe` и `State`:

```haskell
newtype MaybeState s a = MaybeT (State s) a
```

Реализуйте функцию `modifyAndMaybeSumInOrder :: Tree Int -> Int -> MaybeState [Int] Int`, которая должна работать как `sumAndModifyInOrder`, но возвращать результат только в том случае, если количество узлов в дереве не превышает заданного числа `n`, где `n` - второй параметр реализуемой функции.

3. Реализуйте функцию `runMaybeState :: MaybeState s a -> s`, которая сначала запускает вычисления в монадном трансформере `MaybeT`, а затем в монаде `State`.

## Задача на 4

_(Чтобы получить четвёрку, нужно также решить задачу на тройку)_

## Задача на 5

_(Чтобы получить пятёрку, нужно также решить задачи на тройку и четвёрку)_

В файле `src/Tier2/Task.hs` содержится описание простейшей стековой машины...
