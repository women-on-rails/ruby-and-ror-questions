<div align="center">
  <img src="https://img.icons8.com/office/80/000000/ruby-programming-language.png">
  
  <h1>Ruby Questions</h1>
  
    ---

  <span>To do these excercices, I advise you to open up **IRB** to test your answers, here is a [quickstart](https://www.ruby-lang.org/en/documentation/quickstart/).</span></br>
  <span>For each question, copy and paste the "What you have" section in your IRB.</span><br/>
  <span>I chose to use [Struct](https://www.leighhalliday.com/ruby-struct) because they behave kind of like ActiveRecords objects and as a Ruby developer you tend to work on Rails. You can throw me potatoes il you disagree. :potato:</span>

---

  
 </div>

###### 1. Get the year of when these women got a Nobel Prize Award

// What you have
```ruby
Awarded = Struct.new(:year, :name, :category, :contribution)

nobel_prize_awarded_women = [
  Awarded.new(1963, 'Maria Goeppert Mayer', 'Physics', 'for their discoveries concerning nuclear shell structure'),
  Awarded.new(2009, 'Ada E. Yonath', 'Chemistry', 'for studies of the structure and function of the ribosome'),
  Awarded.new(1988, 'Gertrude B. Elion', 'Physiology or Medicine', 'for their discoveries of important principles for drug treatment'),
  Awarded.new(2007, 'Doris Lessing', 'Literature', 'that epicist of the female experience, who with scepticism, fire and visionary power has subjected a divided civilisation to scrutiny')
]
```

// What you need
```ruby
[1963, 2009, 1988, 2007]
```

<details><summary><b>Tips</b></summary>
  <p>
    <strong>Map</strong> method, here is a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
nobel_prize_awarded_women.map { |awarded| awarded.year }
```


  </p>
  </details>
</details>

---
