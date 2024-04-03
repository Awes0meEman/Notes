# Events
Objects by default will inherit all events from their parent object. You can override the event in the child object, or you can additionally inherit and extend an event with the `event_inherited()` function.

# Variables
If you want to have a variable available in the child object that is utilized within the parent object you have to declare variable definitions on the parent, since variables declared in the Create event don't seem to inherit?