<div align="center">
  <img height=80, src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/62/Ruby_On_Rails_Logo.svg/440px-Ruby_On_Rails_Logo.svg.png">

  
  <h1>Ruby on Rails Questions</h1>
  
  ---
  
  These questions go with a Sample App that you can find <a href="https://github.com/women-on-rails/sample_app">here</a>
  
  ---
 </div>

 </div>

##### 1. Find all the posts commented by the first user

<details><summary><b>Tips</b></summary>
  <p>
    You can start with a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">joins</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
Post.joins(:comments).where(:comments => {user: User.first})
```


  </p>
  </details>
</details>

---


##### 2. Find out how many comments they are for each post, be careful for N+1 queries !

<details><summary><b>Tips</b></summary>
  <p>
    One <a href="https://apidock.com/rails/ActiveRecord/QueryMethods/includes">includes</a> a day keep the n + 1 query away.
    <strong>Map</strong> method, here is a <a href="https://www.rubyguides.com/2018/10/ruby-map-method/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
Post.includes(:comments).map { |post| post.comments.size }
```


  </p>
  </details>
</details>

---


##### 3. We want to display the first five posts on our main page, corrects the method in the model Post

<details><summary><b>Tips</b></summary>
  <p>
    It's about setting <a href="https://apidock.com/rails/ActiveRecord/QueryMethods/limit">boundaries</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
  def self.first_five
    limit(5)
  end
```
  </p>
  </details>
</details>

---


##### 4. Find out which users are born before 2010

<details><summary><b>Tips</b></summary>
  <p>
    <a href="https://stackoverflow.com/questions/9624601/activerecord-find-by-year-day-or-month-on-a-date-field">StackOverFlow</a> is strong with this one.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
  User.where('extract(year from birthdate) < ?', 2010)
```
  </p>
  </details>
</details>

---

##### 5. Write a method to dynamically find all users born before a given year

<details><summary><b>Tips</b></summary>
  <p>
    You need to write a scope, here is a <a href="https://www.rubyguides.com/2019/10/scopes-in-ruby-on-rails/">tutorial</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
    scope :born_before, ->(year) { where('extract(year from birthdate) < ?', year) }
```
  </p>
  </details>
</details>

---

##### 6. Make sure that an user can only comment once an article

<details><summary><b>Tips</b></summary>
  <p>
    You need to write a <a href="https://guides.rubyonrails.org/active_record_validations.html#uniqueness">validation</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
     validates :user, uniqueness: { scope: :post,
    message: "can only comment once" }
```
  </p>
  </details>
</details>

---


##### 7. Finds out all the posts without a comment

<details><summary><b>Tips</b></summary>
  <p>
    You need to write a <a href="https://guides.rubyonrails.org/active_record_validations.html#uniqueness">validation</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
     Post.includes(:comments).where(comments: { post_id: nil })
```
  </p>
  </details>
</details>

---


##### 7. Get in a array the content of the comments for the last post

<details><summary><b>Tips</b></summary>
  <p>
    Spoiler alert: it's a one-liner thanks to a <a href="https://apidock.com/rails/ActiveRecord/Calculations/pluck">this</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>

```ruby
     Post.last.comments.pluck(:content)
```
  </p>
  </details>
</details>

---

##### 7. We want to make sure that every time a comment is made on a post, the post is updated

<details><summary><b>Tips</b></summary>
  <p>
    You'll need a callback and, I'm not kidding, this is an <a href="https://www.youtube.com/watch?v=4G6QDNC4jPs">hint</a>.
  </p>

  <details><summary><b>Answer</b></summary>
  <p>
  You'll have a after_save callback like this in comment:

```ruby
    def update_post
      post.touch
    end
```
  </p>
  </details>
</details>

---

