# Slides 9 - Break
```cs
// Spawn 10 new Monsters
for(int i = 0; i < 10; i++) {
  // if there is too many monsters already...
  if(TooManyMonsters()){
    // ...interrupt the loop and continue at ->
    break;
  }
  // This method will not be called anymore, if break is called
  SpawnMonster();
}
// -> the place after the loop
StartGame();
```

This equivalent to:

```cs
for(int i = 0; i < 10; i++) {
  if(TooManyMonsters()){
    goto StopSpawning;
  }
  SpawnMonster();
}
StopSpawning:
StartGame();
```
