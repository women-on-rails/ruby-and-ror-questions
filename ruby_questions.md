<div align="center">
  <img src="https://img.icons8.com/office/80/000000/ruby-programming-language.png">
  
  <h1>Ruby Questions</h1>
  
    ---

  <span>To do these excercices, I advise you to open up **IRB** to test your answers, here is a [quickstart](https://www.ruby-lang.org/en/documentation/quickstart/).</span></br>
  <span>For each question, copy and paste the "What you have" section in your IRB.</span><br/>
  <span>I chose to use [Struct](https://www.leighhalliday.com/ruby-struct) because they behave kind of like ActiveRecords objects and as a Ruby developer you tend to work on Rails. You can throw me potatoes il you disagree. :potato:</span>

---


// What you have
```ruby
Awarded = Struct.new(:year, :name, :category, :contribution, :birthdate)

nobel_prize_awarded_winners = [
  Awarded.new(1963, 'Maria Goeppert Mayer', 'Physics', 'for their discoveries concerning nuclear shell structure', 1906),
  Awarded.new(2009, 'Ada E. Yonath', 'Chemistry', 'for studies of the structure and function of the ribosome', 1939),
  Awarded.new(1988, 'Gertrude B. Elion', 'Physiology or Medicine', 'for their discoveries of important principles for drug treatment', 1918),
  Awarded.new(2007, 'Doris Lessing', 'Literature', 'that epicist of the female experience, who with scepticism, fire and visionary power has subjected a divided civilisation to scrutiny', 1919)
]
```
  
 </div>

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
    <strong>Map</strong> method, here is a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_winners.map { |awarded| awarded.year > 2000 }

```


  </p>
  </details>
</details>

---


##### 3. Get the one whot got her award the youngest


<details><summary><b>Tips</b></summary>
  <p>
    <strong>Inject</strong> method, here is a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">tutorial</a>.
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

##### 4. Sort them by the year they got their award, newest to oldest


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

##### 5. Sort them by their birthdate, oldest to youngest


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
