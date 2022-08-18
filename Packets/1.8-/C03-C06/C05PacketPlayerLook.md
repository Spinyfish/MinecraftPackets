C05PacketPlayerLook is, as you may have guessed, a type of C03PacketPlayer.
In vanilla this is sent when the players rotation, whether on the yaw axis, pitch axis, or both, has changed from last tick.

Like all types of C03's, this updates ground state. 
However just because this packet updates rotation state, it does not mean you should send this packet every time you'd like for your client to change rotation serversided.

Instead you should modify the C03 your client sends every tick. An example of how to do this (using the most common tutorials event system) would be:

```
if(e instanceof EventMotion && e.isPre()) {

	final EventMotion event = (EventMotion)e;

	event.setPitch(-90);

}
```
