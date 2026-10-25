---
notion-id: 221ba0f393fd805c8f86e64b17fd7d21
---
# Defining Data Shape (type, interface, class)

### Types
```tsx
// type alias
type User = { // convention: use PascalCase for types
  id: string;
  name: string;
  avatar: string;
}
```
  
### Interfaces
```tsx
interface User {
  id: string;
  name: string;
  avatar: string;
}
```
  
### Classes
```tsx
class UserClass {
  constructor(
    public id: string,
    public name: string,
    public avatar: string
  ) {}
}
```
  
### When use what?
|   |   |   |   |
|---|---|---|---|
|**Feature**|**Types (**`**type**`**)**|**Interfaces (**`**interface**`**)**|**Classes (**`**class**`**)**|
|**Primary Purpose**|Define shapes/types of data|Define contracts for object shapes|Define both type and implementation|
|**Extensibility**|Cannot be extended after creation|Can be extended/merged (declaration merging)|Can be extended through inheritance|
|**Implementation**|Purely type-level (erased at runtime)|Purely type-level (erased at runtime)|Exists at both type and value level|
|**Runtime Presence**|No - completely erased|No - completely erased|Yes - exists in compiled JavaScript|
|**Can Instantiate**|No|No|Yes (`**new MyClass()**`)|
|**Methods**|Can describe but not implement|Can describe but not implement|Can both describe and implement|
|**Computed Properties**|Supported|Not supported|Supported (in instances)|
|**Union/Intersection**|Can create union (`|`**) and intersection (**`&`) types|Can only be extended/merged, not combined with operators|
|**Mapped Types**|Supported|Not directly supported|N/A|
|**Decorators**|Cannot be decorated|Can be decorated|Can be decorated|
|**When to Use**|- For union/intersection types- For complex type transformations- When needing computed properties|- For object shapes that may be extended- For public API definitions- When declaration merging is needed|- When you need both type and implementation- For OOP patterns (inheritance, encapsulation)- When you need runtime instances|
## **General Guidelines:**
1. **Use interfaces** when:
	- Defining object shapes that may be extended
	- Working with libraries/frameworks that expect interfaces
	- You want declaration merging
2. **Use types** when:
	- You need union or intersection types
	- Creating complex type mappings
	- Need computed properties in your type definitions
3. **Use classes** when:
	- You need to create actual runtime instances
	- You want to use object-oriented patterns
	- You need both behavior (methods) and state (properties) together