<div align="center">
  <img src="https://img.icons8.com/office/80/000000/ruby-programming-language.png">
  
  <h1>Ruby Questions</h1>
  
    ---

  <span>To do these excercices, I advise you to open up **IRB** to test your answers, here is a [quickstart](https://www.ruby-lang.org/en/documentation/quickstart/).</span></br>
  <span>You can also open an IRB [online](https://repl.it/languages/ruby).</span><br/>
  <span>For each question, copy and paste the "What you have" section in your IRB.</span><br/>
  <span>I chose to use [Struct](https://www.leighhalliday.com/ruby-struct) because they behave kind of like ActiveRecords objects and as a Ruby developer you tend to work on Rails. You can throw me potatoes il you disagree. :potato:</span>

---

 
 </div>

// What you have
```ruby
Awarded = Struct.new(:year, :name, :category, :contribution, :birthdate)

nobel_prize_awarded_winners = [
  Awarded.new(1963, 'Maria Goeppert Mayer', 'Physics', 'for their discoveries concerning nuclear shell structure', 1906),
  Awarded.new(2009, 'Ada E. Yonath', 'Chemistry', 'for studies of the structure and function of the ribosome', 1939),
  Awarded.new(2018, 'Frances H. Arnold', 'Chemistry', 'for the directed evolution of enzymes', 1956),
  Awarded.new(1988, 'Gertrude B. Elion', 'Physiology or Medicine', 'for their discoveries of important principles for drug treatment', 1918),
  Awarded.new(1964, 'Dorothy Crowfoot Hodgkin', 'Chemistry', 'for her determinations by X-ray techniques of the structures of important biochemical substances', 1910),
  Awarded.new(2018, 'Olga Tokarczuk', 'Literature', 'for a narrative imagination that with encyclopedic passion represents the crossing of boundaries as a form of life', 1962),
  Awarded.new(2007, 'Doris Lessing', 'Literature', 'that epicist of the female experience, who with scepticism, fire and visionary power has subjected a divided civilisation to scrutiny', 1919),
  Awarded.new(1993, 'Toni Morrison', 'Literature', 'who in novels characterized by visionary force and poetic import, gives life to an essential aspect of American reality', 1931)
]
```
 

##### 1. Get the year of when these women got a Nobel Prize Award

<details><summary><b>Tips</b></summary>
  <p>
    <strong>Map</strong> method, here is a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.map { |awarded| awarded.year }
```


  </p>
  </details>
</details>

---


##### 2. Get all who got their award in the 2000s


<details><summary><b>Tips</b></summary>
  <p>
    <strong>Select</strong> method, here is a <a href="https://www.rubyguides.com/2019/04/ruby-select-method/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.select { |awarded| awarded.year > 2000 }

```


  </p>
  </details>
</details>

---

##### 3. Get how old they were when they got their award


<details><summary><b>Tips</b></summary>
  <p>
    <strong>Map</strong> method, here is a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.map { |awarded| awarded.year - awarded.birthdate }

```

  </p>
  </details>
</details>

---


##### 4. Get the one whot got her award the youngest


<details><summary><b>Tips</b></summary>
  <p>
    <strong>Inject</strong> method, here is a <a href="https://apidock.com/ruby/Enumerable/inject">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.inject do |youngest, awarded|
   (awarded.year - awarded.birthdate) > (youngest.year - youngest.birthdate) ? youngest : awarded
end

```

  </p>
  </details>
</details>

---

##### 5. Sort them by the year they got their award, newest to oldest


<details><summary><b>Tips</b></summary>
  <p>
    <strong>Sort</strong> method, here are some <a href="https://apidock.com/ruby/Array/sort">examples</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.sort { |a, b| b.year <=> a.year }

```

  </p>
  </details>
</details>

---

##### 6. Sort them by their birthdate, oldest to youngest


<details><summary><b>Tips</b></summary>
  <p>
    <strong>Sort</strong> method, here are some <a href="https://apidock.com/ruby/Array/sort">examples</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.sort { |a, b| a.birthdate <=> b.birthdate }

```

  </p>
  </details>
</details>

---


##### 7. Find how many they are in this list by category


<details><summary><b>Tips</b></summary>
  <p>
    There are several ways to deal with it, you can combine two methods: <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">map</a> and <a href="https://rubydoc.info/stdlib/core/Enumerable:tally">tally</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.map(&:category).tally

```

  </p>
  </details>
</details>

---


##### 8. Add an award-winner of your choice (you can find some <a href="https://www.nobelprize.org/prizes/lists/nobel-prize-awarded-women" >here</a>) at the beginning of the array


<details><summary><b>Tips</b></summary>
  <p>
    There are different methods <a href="https://teamtreehouse.com/library/adding-items-to-arrays-2">add elements</a> to an array.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
malala = Awarded.new(2014, 'Malala Yousafzai', 'Peace', 'for their struggle against the suppression of children and young people and for the right of all children to education', 1997)
nobel_prize_awarded_winners.unshift(malala)

```

  </p>
  </details>
</details>


---

##### 9. Get the last element of the array out


<details><summary><b>Tips</b></summary>
  <p>
    You can get a little help from <a href="https://www.youtube.com/watch?v=xVkU8dDSC9w">Hugh Grant</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.pop

```

  </p>
  </details>
</details>


---

##### 10. Get two random winners out of the array


<details><summary><b>Tips</b></summary>
  <p>
    Think about <a href="https://apidock.com/ruby/v2_5_5/Array/sample">hip-hop</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.sample(2)

```

  </p>
  </details>
</details>



---

##### 11. Check if Marie Curie if in the array


<details><summary><b>Tips</b></summary>
  <p>
    You can combine two methods: <a href="https://apidock.com/ruby/Array/include%3F">include?</a> and <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">map</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.map { |awarded| awarded.name }.include?('Marie Curie')

```

  </p>
  </details>
</details>


---


##### 12. Get an array of all last names of the Nobel Prize winnes


<details><summary><b>Tips</b></summary>
  <p>
    You can combine two methods: <a href="https://apidock.com/ruby/String/split">split</a> and <a href="https://apidock.com/ruby/Array/flatten">flatten</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.map { |awarded| awarded.name.split(" ").last }.flatten

```

  </p>
  </details>
</details>
