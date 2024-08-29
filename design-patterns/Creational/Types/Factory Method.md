**Intent**: Define an interface for creating an object, but let subclasses alter the type of objects that will be created.

**Example**: A document creation framework where each type of document (PDF, Word, etc.) has a different factory method.

**Key Points**:
- The method in the interface returns an instance of a product.
- Subclasses override the method to change the class of objects that will be created.
- Promotes loose coupling by reducing dependency on specific implementations.