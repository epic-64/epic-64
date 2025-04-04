My favorite programming languages are Scala and Rust.  

I am using PHP a lot in my day job. It can get things done.  
However my coding style has significantly shifted towards more static typing, generics, domain modeling and functional programming.

Take this example:

In PHP 8
```php
import Carbon\Carbon;

readonly class Person
{
    public string $fullName;
    public int $age;

    public function __construct(public string $firstName, public string $lastName, public Carbon $birthDay)
    {
        $this->fullName = "$firstName $lastName";
        $this->age      = $birthDay->diffInYears(now());

        if ($this->age < 18) {
            throw new RuntimeException("Must be 18+");
        }
    }
}

$person = new Person(firstName: "Jane", lastName: "Doe", birthDay: Carbon::parse('1997-05-17'));
```

In Scala 3
```scala
import java.time.{LocalDate, Period}

case class Person(firstName: String, lastName: String, birthDay: LocalDate):
  val fullName: String = s"$firstName $lastName"
  val age: Int         = Period.between(birthDay, LocalDate.now()).getYears
  require(age >= 18, "Must be 18+")

val person = Person(firstName = "John", lastName = "Doe", birthDay = LocalDate.parse("1997-05-17"))
```

Nothing too fancy is happening here. Just showing that compiled languages don't have to be scary, and instead can feel much more elegant.  
I will soon publish an article with more complex examples of "Scala for PHP devs".

Side projects:
- Runescape-esque ascii game in Scala 3 and Java Lanterna (terminal based)
- fullstack website in Scala 3, Akka Http, Twirl, htmx, vanilla CSS
- 2d game in Rust using Macroquad

Previous side projects (live and ongoing):
- https://rotolist.holonaut.io/ | a todolist application with recurring tasks | Laravel + Livewire
- https://epic-scrolls.holonaut.io/ | a ChatGPT alternative for chatting with OpenAI models, api based | Laravel + Livewire + Web Components
