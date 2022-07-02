## Refactoring from Anemic Domain Model Towards a Rich One

- OVERVIEW:
  - By Vladimir Khorikov. 
  - Domain-driven design. Highly encapsulated domain model.
  - Anemic domain is an anti-pattern. Anemic domain and functional programming. Encapsulation. Refactoring.

- INTRODUCTION:
  - Advanced topic. 
  - Anemic Domain Model: Data and operations seperate from each other.
    - Data: Public 'getters' and 'setters.'
    - Operations: Stateless services.
  - This does not comply with ideas of object-oriented design.
    - Discoverability. Keep methods close to the data.
    - Duplication. Hard to know where methods are lcated. Own implementations.
    - Lack of encapsulation. Most important!
  - Encapsulation: Information hiding. Bundling data and operations together.
    - The act of protecting data integrity. Internal data into an invalid or inconsistent state.
    - Each class has its own set of invariants.
    - e.g.: Square: 4 sides. Equal lengths. Angles are of 90 degrees.
    - Encapsulation: No operation should be able to violate the invariants.
    - Why is encapsulation so important? Complexity.
      - Decrease the speed of development.
      - Increase the number of bugs.
      - Damage the ability to respond to business needs.
  - Does an anemic domain model automatically entail lack of encapsulation?
    - Data: Person. 
    - Services: PersonService. No restrictions. Potential duplication.
  - Attribute the task of maintaining data integrity to the classes containing that data.
  - Advantages of anemic domain model:
    - Intuitive. Developers pick it up naturally.
    - Easy to implement. Fast development, at least initially.
  - NOTE: Bounded contexts can implement different strategies.
  - Anemic domain model & functional programming:
    - Immutable data structures:
    - Operations upon data are kept separately:
    - e.g.: Segrated data and associated operations:
    ```csharp
      public class Square
      {
        public readonly double SideLength;
        public Square(double sideLength)
        {
          if (sideLength <= 0)
          {
            throw new Exception($"Invalid square side length: {sideLength}.");
          }
          SideLength = sideLength;
        }
      }
      public class Services
      {
        public static double CalculateArea(Square square)
        {
          return square.SideLength * square.SideLength;
        }
      }
    ````
    - Immutability: No need to worry about corruption of internal state. Impossible to currpupt something that cannot be changed.
    - No need in encapsulation.
  - Object-oriented programming makes code uderstandable by encapsulating moving parts. 
  - Functional programming makes code understandable by minimizing moving parts.
  - How about discoverability? Can be mitigated using conventions.
  - Summary:
    - Anemic domain model keeps data and operations seperate from each other. Two classes. Properties and stateless services.
    - Tough discoverability. Potential duplication. Encapsulation.
    - Encapsulation is the act of protecting the data integrity. Otherwise hard to maintain code correctness.
    - Anemic domain always entails the lack of encapsulation.
      - EXCEPTION: Immutable classes.

- ANEMIC DOMAIN MODEL:
  - Sample project.

- DECOUPLING FROM DATA CONTRACTS:
- USING VALUE OBJECTS AS DOMAIN MODEL BUILDING BLOCKS:
- PUSHING LOGIC FROM SERVICES TO DOMAIN CLASSES:
- ORGANIZING THE APPLICATION SERVICES LAYER:
- DOMAIN MODELING BEST PRACTICES: