# Slides 10 - Continue

```cs
for(int i = 0; i < numberOfPlayers; i++) {
  // if the player has disconnected already...
  if(PlayerIsDisconnected(i)){
    // then interrupt this loop iteration and continue with the next iteration ->
    continue;
  }
  // the code only reaches here, if the player #i has not disconnected :)
  SpawnPlayer(i);
  
  // -> the next iteration will begin after the end
}
```

This equivalent to:

```cs
for(int i = 0; i < numberOfPlayers; i++) {
  if(PlayerIsDisconnected(i)){
    goto SkipPlayer;
  }
  SpawnPlayer(i);

  SkipPlayer:;
}
```