![JCA Banner](http://i.imgur.com/IuMFp5Z.png "Java Challonge API")

# JCA (Java Challonge API)
JCA strives to make [Challonge](https://challonge.com/) interactions through Java a lot easier, cleaner, and more efficient.

## Creating a Tournament
To initialize a tournament, you must run something of the sorts:
```java
Tournament tourn = new Tournament()
    .setAPIKey("api key goes here")
    .setName("Swedz's Tournament")
    .setType(Type.SINGLE)
    .setURL("single_elim")
    .setDesc("Some dank tournament stuffs")
    .withPlayers(new String[] {
        "Dank",
        "Memes"
    }).build();
```
This will create a tournament at the link challonge.com/single_elim/ with the players Dank and Memes, description of "Some dank tournament stuffs", and with a display name of "Swedz's Tournament".

## Starting and Ending Tournaments
To start and/or end a tournament, simply use one of these functions:
```java
tourn.start();
...
tourn.end();
```
This will cause the tournament to begin or end on the webpage.

## Chosing Winners for Matches
Matches are a little trickier than the other things, so I have tried my hardest to make this as easy for you as possible. Simply, supply the tournament url (e.g: single_elim), match number that is currently running, and the player who won the match. Or, if it is a tie, supply both players.
```java
JCA.matches().winner(1, "Dank");
...
JCA.matches().tie(1, "Dank", "Memes");
```
Note, when supplying the match id, you want to specify the global match number. So, you would need to make an int variable (starting at 1) that will be added to every time a game ends. And that would be the match id you supply to the JCA#matches()#winner() or JCA#matches()#tie() methods.

## Maven Setup
To use JCA in your Maven project, download the src for JCA, export it as a JAR File (named JCA.jar), put the jar in your /src/main/resources/ directory, and in your pom.xml, add this to your dependencies:
```xml
<repository>
  <id>Java Challonge API</id>
  <url>file://${basedir}/src/main/resources/JCA-0.1.jar</url>
</repository>
...
<dependency>
  <groupId>me.Swedz</groupId>
  <artifactId>JCA</artifactId>
  <version>0.1</version>
</dependency>
```
Once you do this, you can use the API in your project as much as you want!
Note that the <repository> and <dependency> must go in their respective sections.
Also, be sure to put JCA-0.1.jar into your local repository:
```
C:\Users\{Username}\.m2\repository\me\Swedz\JCA\0.1\JCA-0.1.jar
```
Include the jar in your /src/main/resources/ as well.

## Known Problems
All projects have their little quirks and issues. And these are JCA's:

- Not Asynchronous
- Adding participants doesn't use [bulk_add](https://api.challonge.com/v1/documents/participants/bulk_add)

*Credit is appreciated :)*
