#  Homework 8 — The Haunted Tower: Ascending the Floors

##  Overview
This project is a tower-climbing RPG implemented in Java. The main goal is to demonstrate the practical use of two behavioral design patterns: **State** and **Template Method**. Heroes ascend the tower floor by floor, facing different challenges while managing internal status effects that change dynamically.

---

##  Design Patterns

### 1. State Pattern
Governs **intra-entity behavior changes**. Each hero carries a `HeroState` that modifies combat performance. 
* **Self-Transitions:** The states are responsible for their own transitions (e.g., poison wears off after 3 turns, or stun clears).
* **Impact:** Modifies outgoing/incoming damage and determines if a hero can take an action.

### 2. Template Method Pattern
Governs **inter-activity algorithm structure**. The `TowerFloor` abstract class defines a fixed skeleton for exploring any floor.
* **The Template Method:** `explore(List<Hero> party)` is marked as `final`.
* **The Steps:** 1. `announce()` — Initial message.
    2. `setup()` — Abstract step for floor preparation.
    3. `resolveChallenge()` — Abstract step for the main logic (combat/rest).
    4. `awardLoot()` — Reward phase (conditional hook).
    5. `cleanup()` — Optional hook for post-floor logic.

---

##  Project Structure

| File | Description |
| :--- | :--- |
| `HeroState.java` | Interface defining the contract for hero states. |
| `TowerFloor.java` | Abstract base class containing the **Template Method**. |
| `FloorResult.java` | Data class representing the outcome of a floor. |
| `Hero.java` | Concrete class for heroes, managing their current `HeroState`. |
| `Monster.java` | Concrete class for enemies encountered on floors. |
| `TowerRunResult.java` | Summary of the entire tower run. |
| `Main.java` | Entry point that initializes the tower and runs the simulation. |

---

##  Quick Start

### Prerequisites
* JDK 11 or higher installed.
* Any Java IDE (IntelliJ IDEA recommended).

### Compilation
From the project root directory, run:
```bash
javac -d out $(find src -name "*.java")
