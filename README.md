# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.
```swift
enum iosDeviceType {
case iPhone(String)
case iPad(String)
case iWatch(Int)
}
var myDevice = iosDeviceType.iPhone("x")
switch myDevice {
case .iPhone(let modelType):
print("this is an iPhone \(modelType)")
case .iPad(let modelType):
print("this is an iDad \(modelType)")
case .iWatch(let modelType):
print("this is an iWatch \(modelType)")
}


```

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.

## Question 2

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.
```swift
enum Shape: String {
case triangle = "3 sides"
case square = "4"
case pentagon = "5"
case hexagon = "6"

func findSide () -> String{
switch self {
case .triangle:
return  Shape.triangle.rawValue
case .square:
return Shape.square.rawValue
case .pentagon:
return Shape.pentagon.rawValue
case . hexagon:
return Shape.hexagon.rawValue
}
}
}
var myFavoritePolygon = Shape.triangle.rawValue
print(myFavoritePolygon)

```
c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.
```swift
enum Shape{
case triangle(Int)
case square(Int)
case pentagon(Int)
case hexagon(Int)

func findPerimeter () -> Int{
switch self {
case .triangle(let length):
return length * 3
case .square(let length):
return length * 4
case .pentagon(let length):
return length * 5
case .hexagon(let length):
return length * 6
}
}
}
let lengthOfMypentagon = Shape.pentagon(5).findPerimeter()
print(lengthOfMypentagon)

```


## Question 3

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.


## Question 4

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

// your code here
enum Direction {
case up
case down
case left
case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]
for direction in steps {
switch direction {
case .up:
location.y += 1
case .down:
location.y -= 1
case .left:
location.x -= 1
case .right:
location.x += 1
}
}
print("the final loications is \(location)")

```


## Question 5

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper
```swift
enum HandShape {
case rock , paper , scissors
}

enum MatchResult {
case win, draw, lose

}

func matchWinner(pOne: HandShape, pTwo: HandShape)-> MatchResult {
switch pOne {
case .rock:
switch pTwo {
case .rock: return .draw
case .paper: return .lose
case .scissors: return .win
}
case .paper:
switch pTwo {
case .rock: return .win
case .paper: return .draw
case .scissors: return .lose
}
case .scissors:
switch pTwo {
case .rock: return .lose
case .paper: return .win
case .scissors: return .draw
}

}
}

var albert = HandShape.scissors
var bert = HandShape.rock
print(matchWinner(pOne: albert, pTwo: bert))

```

## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
var sum = 0
for i in moneyArray {
sum += i.0 * i.1.rawValue
}
```

b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.
```swift
enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25

func toOneHundred() ->Int{
switch self{
case .penny:
return 100
case .nickle:
return 10
case .dime:
return 20
case .quarter:
return 4
}

}
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
(15,.nickle),
(3,.quarter),
(20,.penny),
(3,.dime),
(7,.quarter)]


var myCoin =    CoinType.quarter.toOneHundred()

print(myCoin)


```

## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.


## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

c) Write code that prints the train letter or number of your instance of `MetroLine`.


## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.
