### Where to Use

Use the Facade Pattern in the following scenarios:

- When you want to provide a simple interface to a complex system or subsystem.
- When you want to hide the complexities of a system and provide a high-level interface for clients.
- When you need to decouple client code from the implementation details of a subsystem.

### Code Explanation

#### Facade Pattern Implementation

##### Step 1: Identify a Complex Subsystem

Consider a scenario where we have a complex home theater system consisting of multiple components such as DVD player, projector, lights, and sound system.

##### Step 2: Implement the Facade

```java
// Facade
public class HomeTheaterFacade {
    private DVDPlayer dvdPlayer;
    private Projector projector;
    private Lights lights;
    private SoundSystem soundSystem;

    public HomeTheaterFacade() {
        this.dvdPlayer = new DVDPlayer();
        this.projector = new Projector();
        this.lights = new Lights();
        this.soundSystem = new SoundSystem();
    }

    public void watchMovie(String movie) {
        System.out.println("Get ready to watch a movie...");
        lights.dim();
        projector.on();
        soundSystem.on();
        dvdPlayer.play(movie);
    }

    public void endMovie() {
        System.out.println("Shutting down the movie...");
        dvdPlayer.stop();
        projector.off();
        lights.on();
        soundSystem.off();
    }
}

```

- The `HomeTheaterFacade` class acts as a facade that provides a simplified interface to the complex home theater system.

##### Step 3: Client Code

```java
public class FacadePatternExample {
    public static void main(String[] args) {
        HomeTheaterFacade homeTheater = new HomeTheaterFacade();

        homeTheater.watchMovie("Inception");
        System.out.println("\nEnjoying the movie...\n");

        homeTheater.endMovie();
    }
}

```

