I needed to provide Bluetooth to a Docker container. However, I didn't like the ways I've found:

a. Adding excessive privileges to the container.
b. Passing whole system D-Bus to the container, essentially giving the container quite much power.

As a result, I've decided to create a separate D-Bus instance just for Bluez.

## Potential drawbacks

### My knowledge of D-Bus is limited

I've looked for the right way to do that, but I've found nothing. Due to my limited knowledge of
D-Bus, I might be still exposing some excessive privileges to the Docker container. However, the
impact of this should be limited by running D-Bus under a separate user with limited privileges.

If you know I am doint something wrong, please create an issue. If you think I am doing it right
and you can prove it, please create an issue, too, because I'd like to update the documentation.

### Bluez itself is not sandboxed

Bluez seems to need root privileges, and I cannot do much about that.

### Using session D-Bus socket as the system one

I've created a session D-Bus instance (because it seemed that it is more suitable for unprivileged
daemon), but use it as a privileged one, because BlueZ needs it. This is quite ugly.

