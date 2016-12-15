# Kotlin Lambda

> A lambda expression or an anonymous function is a "function literal", i.e. a function that is not declared, but passed immediately as an expression. Consider the following example:
>
> --  [<cite>kotlin docs</cite>](https://kotlinlang.org/docs/reference/lambdas.html#lambda-expressions-and-anonymous-functions)

## Expression Syntax

Et lambda udtryk er altid omgivet af curly brackets. På venstre side af pilen har vi input-parametrene, her 2 Ints (x og y) og på højre side har vi udtrykkets body.

``` kotlin
val sum = { x: Int, y: Int -> x + y }
```


Hvis et lambda udtryk kun har én parameter kan man undlade at definere parametre og kan så bruge `it` som substitut for denne.
Som vist i eksemplet nedenfor

``` kotlin
ints.filter { it > 0 }
```


## Eksempler

I dette eksempel har vi en funktion der, som input parametre, tager en Collection og et lambda udtryk med to tilhørende parametre af typen T og som returnerer en Boolean.

``` kotlin
fun <T> max(collection: Collection<T>, less: (T, T) -> Boolean): T? {
    var max: T? = null
    for (it in collection)
        if (max == null || less(max, it))
            max = it
    return max
}
```

funktionen `max` itererer over `collection`. For hvert element kaldes det medsendte lambda udtryk med variablerne `max` og `it` (hvor `it` er det nuværende element i iterationen). 


``` kotlin
val strings = listOf("Fish", "Cat", "Giraffe")
max(strings, { a, b -> a.length < b.length })
```

I dette eksempel kalder vi metoden `max` med 2 parametre: `strings` og ét lambda udtryk. Metoden returnerer i dette tilfælde `Giraffe`, som er det længste ord i listen (vores lambda udtryk sammenligner ordenes længder)

``` kotlin
val ints = listOf(3, 5, 1, 6)
println(max(ints) {a, b -> a < b})
```
I dette eksempel gør vi det samme som overstående bare med heltal istedet

