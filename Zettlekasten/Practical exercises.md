### **Exercise 1: Counter App**
- **Task:**  
    Create a counter app using a `StatefulWidget`. Add Increment and Decrement buttons and display the current count. Bonus: prevent the counter from going below 0.

- **Follow-ups (questions while checking):**
    1. Why did you choose a `StatefulWidget` instead of `StatelessWidget`?
    2. If we wanted this counter to persist when the app restarts, how would you implement that?

---

### **Exercise 2: ListView**
- **Task:**  
    Build a `ListView` of 10 items with a title and subtitle. When an item is tapped, show a `SnackBar` with the item name.
    
- **Follow-ups:**
    1. How would you optimize this `ListView` if the list had 10,000 items?
    2. What is the difference between `ListView.builder` and `ListView` with children, and why would you use one over the other?

---

### **Exercise 3: Form Validation**
- **Task:**  
    Build a form with two fields: Email and Password. Validate that Email contains “@” and Password is at least 6 characters. Show an error message if validation fails.
    
- **Follow-ups:**
    1. How would you handle more complex validations (e.g., password strength, multiple rules per field)?
    2. How would you make the validation logic reusable across multiple forms?

---

### **Exercise 4: Mock API Integration**
- **Task:**  
    Use a mock JSON list of objects (`id` and `name`). Fetch and display in a `ListView`. Show a loading indicator while fetching.
    
- **Follow-ups:**
    1. How would you handle network errors or retries?
    2. How would you implement pagination or infinite scrolling for a large API dataset?

---

### **Exercise 5: Unit Test**

- **Task:**  
    Write a Dart function to calculate the sum of numbers in a list. Write a unit test to verify the function works correctly.
    
- **Follow-ups:**
    1. How would you test edge cases (e.g., empty list, negative numbers, very large numbers)?
    2. How would you structure tests if this function became part of a bigger service with multiple functions?

Links:

202511082200

