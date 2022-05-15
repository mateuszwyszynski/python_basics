# **Słowniki w Pytohnie**
Poprzedni notebook (week 9) dotyczył `list` w Pythonie. W tym notebooku powiemy sobie coś o `słownikach`, czyli kolejnej strukturze danych.
Przypomnijmy najpierw czym były `listy`. 

`Lista` to struktura danych w Pythonie, która jest zmienną, uporządkowaną sekwencją elementów. Listy służą do przechowywania wielu elementów w jednej zmiennej. 

Listy są `uporządkowane`, można je zmieniać (są `edytowalne`) i zezwalają na `zduplikowane wartości`.

Elementy listy są `indeksowane`, pierwsza pozycja ma indeks `[0]`, druga pozycja ma indeks `[1]` itd.


Listę inicjalizujemy `kwadratowymi nawiasami`.


## Przykład


```python
fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
print(fruits)
```

    ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']



```python
fruits[0]  # pierwszy element listy
```




    'orange'



# **Słownik (dictionary)**

Teraz powiemy sobie czym są słowniki w Pythonie.

`Słowniki` służą do przechowywania wartości w parach `klucz:wartość`.

Słownik to zbiór `uporządkowany`, `zmienny` i `nie pozwalający na duplikaty`.

Słownik inicjalizujemy `klamrowymi nawiasami`.


# **Tworzenie słownika w Pythonie**

Tworzenie słownika jest tak proste, jak umieszczanie elementów w nawiasach klamrowych `{ }` oddzielonych przecinkami.

Każdy element słownika to para (key: value). `Key` oznacza klucz w słowniku, a `value` reprezentuje jego wartość.

Chociaż `wartości` mogą być dowolnego typu i mogą się powtarzać, `klucze` muszą być typu `niezmiennego` i muszą być `unikatowe`.

## Przykład


```python
my_dict = {    # tworzenie słownika przy użyciu nawiasów klamrowych
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
```

W powyższym słowniku `my_dict` kluczami są: `brand`, `model` i `year`, a odpowiadającymi im wartościami są: `Ford`, `Mustang` i `1964`.
Zauważ, że po danym kluczu zawsze dajemy dwukropek, a dopiero potem wartość.

# Tworzenie słownika przy użyciu dict()

`Słownik` w Pythonie może zostać stworzony przy użyciu wbudowanej funkcji `dict()`. Funkcja ta jako argumenty przyjmuje pary `key`,`value`.

## Przykład


```python
x = dict(brand = "Ford", model = "Mustang", year = "1964") #tworzenie słownika przy użyciu dict()
```

Zauważ, że ten sposób inicjalizaji słownika ma pewne różnice:



*   kluczy (`keys`) nie przekazujemy jako stringi,
*   rolę dwukropka pełni znak równości,
*   funkcji `dict()` przekazujemy pary bez zamykania ich w nawias klamrowy.





# Dostęp do elementów ze słownika
Podczas gdy indeksowanie jest używane z innymi typami danych  (np. `listami`) w celu uzyskania dostępu do `wartości`, słownik używa `kluczy` (tzn. indeksowanie jak w listach, nie zadziała). `Klucze` mogą być używane w nawiasach kwadratowych `[ ]` lub z metodą `get()`.
Jeśli np. chcielibyśmy w słowniku `my_dict` znaleźć `wartość` dla `klucza` `brand` możemy to zrobić tak:


```python
my_dict['brand'] # wartość pod kluczem 'brand'
```




    'Ford'



Lub przy użyciu metody `get()`:


```python
my_dict.get('brand')
```




    'Ford'



Jeśli użyjemy nawiasów kwadratowych `[ ]` dla klucza, którego nie ma słowniku, wyskoczy nam błąd `KeyError`. Metoda `get()` zwróciłaby `None`.


```python
my_dict['bwm']  #klucza 'bwm' nie ma w słowniku --> KeyError
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-13-04a0b9c4a66f> in <module>()
    ----> 1 my_dict['bwm']
    

    KeyError: 'bwm'



```python
print(my_dict.get('bmw'))   # klucza 'bwm' nie ma w słowniku --> get() zwraca None
```

    None



```python
my_dict[0]  #indeksowanie jak listach nie zadziała --> KeyError
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-110-12cd0ddeaa4b> in <module>()
    ----> 1 my_dict[0]  #indeksowanie jak listach nie zadziała -->
    

    KeyError: 0


# Zmienianie i dodawanie elementów słownika

Słowniki są `zmienne` (edytowalne). Możemy dodawać nowe pozycje lub zmieniać wartość istniejących pozycji za pomocą operatora przypisania, czyli `=`.

Jeśli `klucz` jest już obecny, `aktualizowana` jest istniejąca `wartość`. W przypadku braku klucza do słownika dodawana jest nowa para (klucz: wartość).

## Przykład


```python
# Zmienianie i dodawanie elementów słownika
my_dict = {   
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}

# aktualizowanie wartości
my_dict['year'] = 1987

print(my_dict)
```

    {'brand': 'Ford', 'model': 'Mustang', 'year': 1987}


Zmieniliśmy wartość dla `klucza` `year` na 1987. Podobnie możemy zmienić pozostałe wartości kluczy.


```python
my_dict['brand'] = 'Audi' #aktualizujemy wartośc dla klucza "brand" na "Audi"

my_dict['model'] = 'RS3' #aktualizujemy wartośc dla klucza "model" na "RS3"

my_dict['year'] = 2019 #aktualizujemy wartośc dla klucza "year" na "2019"

print(my_dict)
```

    {'model': 'RS3', 'year': 2019, 'brand': 'Audi'}


# Usuwanie elementów ze słownika

Możemy usunąć konkretną pozycję ze słownika za pomocą metody `pop()`. Ta metoda usuwa element z podanym kluczem. Na koniec wyświetla wartość usuniętej pary.



```python
my_dict.pop('brand') #usuwa klucz 'brand' wraz z jego wartością a na koniec printuję tę wartość 
```




    'Audi'



Metoda `popitem()` usuwa element, który był ostatnio wstawiany do słownika. Na koniec wyświetla usuniętą parę.


```python
my_dict['color'] = 'red' #wstawmy nową parę: color: red
print(my_dict)
```

    {'model': 'RS3', 'color': 'red'}



```python
my_dict.popitem()  # usuwa ostanio wstawianą parę, czyli color: red.
```




    ('color', 'red')




```python
my_dict # ze słownika zniknęła para color: red
```




    {'model': 'RS3'}



W celu usunięcia wszystkich elementów ze słownika możemy użyc metody `clear()`.


```python
year_of_creation = {'Python': 1993, 'JavaScript': 1995, 'HTML': 1993}  # tworzymy jakiś słownik
print(year_of_creation)
```

    {'Python': 1993, 'JavaScript': 1995, 'HTML': 1993}



```python
year_of_creation.clear()  # metoda clear usunie wszystkie elementy (pary key:value)
print(year_of_creation)
```

    {}


# **Metody słownika Pythona**

Poniżej zestawione są metody dostępne ze słownikiem. Niektóre z nich zostały już wykorzystane w powyższych przykładach.

| **Metoda** 	| **Opis**                                          	|
|------------	|---------------------------------------------------	|
| keys()     	| Zwraca widok kluczy słownika          	|
| values()   	| Zwraca widok wartości w słowniku       	|
| items()    	| Zwraca widok zawierający pary klucz-wartość       	|
| get()      	| Zwraca wartość określonego klucza                 	|
| pop()      	| Usuwa element z określonym kluczem                	|
| popitem()  	| Usuwa ostatnią wstawioną parę klucz-wartość       	|
| clear()    	| Usuwa wszystkie elementy ze słownika              	|
| copy()     	| Zwraca kopię słownika                             	|
| fromkeys() 	| Zwraca słownik z określonymi kluczami i wartością 	|

## Metody `keys()`, `values()` i `items()`

Powyższe metody zwracają widok na odpowiednio: klucze, wartości i elementy słownika (pary `key:values`). Zwrócone przez nich obiekty `nie są listami` więc nie można ich indeksować.

# Przykład


```python
my_dict = {   
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}

dict_keys = my_dict.keys() #przypisujemy zmiennej dict_keys klucze słownika my_dict
print(dict_keys)
```

    dict_keys(['brand', 'model', 'year'])



```python
dict_values = my_dict.values() #przypisujemy zmiennej dict_values wartości słownika my_dict
print(dict_values)
```

    dict_values(['Ford', 'Mustang', 1964])



```python
dict_items = my_dict.items() #przypisujemy zmiennej dict_items elementy słownika my_dict
print(dict_items)
```

    dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])



```python
dict_keys[0] # metody keys, values, items nie pozwalają na indeksowanie --> TypeError
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-52-995a0b2517a3> in <module>()
    ----> 1 dict_keys[0] # metody keys, values, items nie pozwalają na indeksowanie --> TypeError
    

    TypeError: 'dict_keys' object is not subscriptable


# **Iteracja przez słownik**

Możemy iterować się przez każdy klucz w słowniku za pomocą pętli `for`. 

## Przykład


```python
for key in my_dict:  #gdybyśmy dali my_dict.keys() rezultat byłby taki sam
  print(key)
```

    brand
    model
    year


Aby przeiterować się po wartościach, możemy wykorzystać metodę `values()`.


```python
for value in my_dict.values():
  print(value)
```

    Ford
    Mustang
    1964


Podobnie możemy itereować się po `elementach` słownika (parach `key:value`)

## Przykład


```python
for element in my_dict.items():
  print(element)
```

    ('brand', 'Ford')
    ('model', 'Mustang')
    ('year', 1964)


# Metoda fromkeys()

Metoda `fromkeys()` jest bardzo przydatną podczas tworzeniu słowników. Pozwala ona stworzyć słownik ze zdefniowanej wcześniej listy i wartości, która ma zostać przypisana każdemu kluczowi.

## Przykład


```python
marks = {}  # tworzymy pusty słownik
names = ['John', 'Mark', 'Matthew 1', 'Matthew 2', 'Peter 1', 'Peter 2', 'Charles']
grades = 1
marks = marks.fromkeys(names, grades)  # wypełniamy pusty słownik
print(marks)
```

    {'John': 1, 'Mark': 1, 'Matthew 1': 1, 'Matthew 2': 1, 'Peter 1': 1, 'Peter 2': 1, 'Charles': 1}



```python
marks["Charles"] = 6
print(marks)
```

    {'John': 1, 'Mark': 1, 'Matthew 1': 1, 'Matthew 2': 1, 'Peter 1': 1, 'Peter 2': 1, 'Charles': 6}


# Wbudowane funkcje słownika

Wcześniej poznalismy już parę podstawowych funkcji w Pythonie m.in. `len()` i `sorted()`. Funkcja `len()` zwraca długość struktury danych, a `sorted()` sortuje rosnąco. W przypadku słowników, funkcja `sorted()` zwraca listę posortowanych `wartości` (domyślnie rosnąco).

## Przykład





```python
ages = dict(Maria = 17, Peter = 22, Donald = 14, John = 32, Linda = 29, Sandra = 25)
print(ages)
```

    {'Maria': 17, 'Peter': 22, 'Donald': 14, 'John': 32, 'Linda': 29, 'Sandra': 25}



```python
len(ages)
```




    6




```python
sorted(ages) # zwraca listę wartości (imion) od najmłodszych do najstarszych
```




    ['Donald', 'John', 'Linda', 'Maria', 'Peter', 'Sandra']



# **Zadanie Przykładowe 1**

Stwórz funkcję `names_length`, która przyjmuję jeden argument, `listę` imion, i `zwraca` słownik, gdzie każdy element tego słownika to para `imię: długość imienia`. Tzn. rolę `key` pełni imię, a rolę `value` pełni liczba liter w imieniu.

## Rozwiązanie


```python
def names_length(names):
  names_dict = {}  # tworzymy pusty słownik
  for name in names:  # iterujemy się po imionach w liście
    names_dict[name] = len(name)  # dodajemy parę name : len(name) do słownika 
  return names_dict
```

Sprawdźmy działanie naszej funkcji:


```python
names = ['John', 'Mark', 'Matthew', 'Peter', 'Charles']
```


```python
names_length(names)
```

# **Zadanie Przykładowe 2**

Stwórz funkcję `top_3`, która przyjmuje jeden argument (słownik zawierający pary kraj: liczba ludności w mln) i zwraca nazwy trzech najbogatszych krajów.

## Rozwiązanie


```python
def top_3(dictionary):
  sorted_dictionary = sorted(dictionary, reverse = True)
  top_3_keys = sorted_dictionary[:3]  # bierzemy pierwsze 3 elementy z posortowanej listy wartości
  return top_3_keys


```


```python
countries = dict(Croatia = 4.1, Czechia = 10.7, Finland = 5.5, Nepal = 29.1, Spain = 46.7, Poland = 37.8)
```


```python
top_3(countries)
```




    ['Spain', 'Poland', 'Nepal']



# **Podsumowanie**

`Słowniki` służą do przechowywania wartości danych w parach `klucz: wartość`.

Słownik to zbiór `uporządkowany`, `edytowalny` i `nie pozwalający na duplikaty`.

