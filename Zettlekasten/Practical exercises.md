# **Exercise 1: Counter App**

### **Task:**

Create a counter app using a `StatefulWidget`.  
Add **Increment**, **Decrement**, and **Reset** buttons.  
Prevent the counter from going below **0** and above **20**.  
Show a SnackBar when limits are reached.

### **Middle-Level Add-ons (optional):**
- Use `ValueNotifier` instead of `setState` (shows state-management awareness).
- Extract widgets into separate classes (shows architecture thinking).
- Add unit tests for counter logic (shows testability mindset).

### **What you evaluate:**
- Clean code, naming, widget extraction
- Understanding of state vs UI
- Ability to add constraints
- Does he overcomplicate or solve cleanly?

---

# **Exercise 2: ListView**

### **Task:**

Create a list of **50 items** with title + subtitle.  
Tap shows a SnackBar.  
Add a **search bar** to filter items in real time.

### **Middle-Level Add-ons:**
- Use `ListView.builder`
- Use `debounce` for search
- Extract list item to a separate widget
- Add empty state when nothing matches the search

### **What you evaluate:**
- Ability to scale up (search + builder)
- Separation of UI and logic
- Performance awareness

---

# **Exercise 3: Form Validation**

### **Task:**

Create a login form with Email + Password.  
Validation:
- Email must contain “@”
- Password ≥ 6 chars
- Disable Submit button until form is valid
- On submit → show loading indicator → fake delay → success

### **Middle-Level Add-ons:**
- Use `Form` + `GlobalKey<FormState>` properly
- Use custom validator classes (reusable)
- Add `autovalidateMode: onUserInteraction`
- Password visibility toggle

### **What you evaluate:**
- Clean validation approach
- UX thinking (disabling button)
- State handling for loading

---

# **Exercise 4: Mock API Integration**

### **Task:**

Fetch JSON data from a mock API (local file or API like jsonplaceholder).  
Show loading + error + success states.  
Add a refresh button.

### **Middle-Level Add-ons:**
- Use `FutureBuilder` cleanly
- Introduce data model + JSON parsing
- Add retry logic
- Add pagination (load more on scroll end)

### **What you evaluate:**
- Asynchronous code quality
- Error-handling approach
- Data modeling
- Ability to implement pagination (very Middle-level)

---

# **Exercise 5: Unit Tests**

### **Task:**

Write a function that:
- Accepts a list of numbers
- Returns:  
    `{sum: X, average: Y, max: Z}`

Write **unit tests** that cover:
- empty lists
- negative numbers
- large numbers
- null input (if you allow it)

### **Middle-Level Add-ons:**
- Use proper test grouping
- Test for exceptions
- Use setup/teardown if needed
- Document the function

### **What you evaluate:**
- Test structure
- Understanding of edge cases
- Naming and clarity
- Ability to think “service layer” logic

Links:

202511082200

