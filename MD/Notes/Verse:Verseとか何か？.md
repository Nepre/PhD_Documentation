# Verseとか何か？

## Speaker
Magnus Enebakk

## 01 What is verse and why
Programming language for gameplay code (used on Fortnite already)
- Easy to learn
- Strongly typed (errors at compile time)
- Everything is an expression
  - if / then like on python
- Inmmutable by default
- Multi-paradigm
- Effect specifiers
funciton effect specifiers <decides> <transacts>

Design to be backwards compatible. If you publish something you have to keep it backwards compatible, otherwise Epic will jump in and stop you.

Gameplay waits for time and events (sleep, await, race, sync)


## 02 VERSE IN UE6

Verse and Scene Graph ship in UEFN now. UE6 brings both together, with early access planned 2027

UE5  + (verse and scene graph)

Verse is for gameplay but you can still use C++ to expose API for your gameplay functions.

UE6 is verse and scenegraph first and they will continue to support UE5.

## 03 Key language features

``
MaxPlayers:int = 16
Greeting := "Helo, Unreal"  # type inferred
var Health:float = 100.0    # MUTABLE
``

Everything is an expression

``
Doubled := for (X : array{2,3,4}){x * 2}
``
Effect specifiers

<computes> -> no side effects: same input, same output (math, conversions)
<reads> -> Can read a mutable state but cannot change it
...

A failed expression has no value: no exception, no null. Faliable code only compiles inside a failure context, so you can't forget to handle it.

```
if:
  vehicle := Player.GetVehicle[]
  Weapon := Vehicle.GetComponent[weapon_component]
  Projectile := Weapon.GetLoaded[]
then:
  Projectile.Fire(Target)
```

```
Targets := for:
  Enemy : AllEnemies
  Enemy.IsAlive[]
  Enemy.IsVisibleFrom[PlayerPos]
  Distance(Enemy.Position, PlayerPos) < Range >

do:
  Enemy

DoSomething(Enemy)
```

We can have failure in every day code. None of these change state. If the check fails, the if body is skipped, or or gives you a fallback.

You can write your own failiable functions

```
GetDamage(P:player, Slot:int)<decides><reads>:int =
# insert fail states here
  Shield.Damage[damage]   # fails if the damage is absorved (?)
...
```

The idea is to have everything as a series of failure states, so you can do all of them but if the last one fails we just roll back everything.

Planned: Speculate will return the error so we can show it to the player, while running everything but returning the error codes for us to show.

We can see an example of things that would have been different functions. In the tick function of an asset it would have run a check timer, instead of the sleep. It would have had to create some events or states for the door been fully open... So the code is easier to read.ß 
```
OpenVault()<suspends>:void =
  Alarm.Play()
  Sleep(2.0)
  Door.SlideOpen()
  Guard.ArrivedEvent.Await()
  Alarm.Stop()
```

### Structured concurrency

sync: AND: wait for all
race: OR: first one wins
rush: First answer, other keep going
branch: Background, within the scope