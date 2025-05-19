## **Web Accessibility (WCAG) - Complete Guide**

### **🔹 What is WCAG?**

WCAG (**Web Content Accessibility Guidelines**) is a **set of standards** developed by the W3C to ensure that websites are accessible to people with disabilities.

📌 It provides recommendations to make digital content accessible for users with:

- **Visual impairments** (blindness, low vision, color blindness)
    
- **Hearing impairments** (deafness, hard of hearing)
    
- **Motor disabilities** (difficulty using a mouse or keyboard)
    
- **Cognitive impairments** (dyslexia, memory issues, learning disabilities)
    

---

## **1️⃣ The Four WCAG Principles**

WCAG is built on **4 core principles** (POUR):

|Principle|Explanation|
|---|---|
|**P**erceivable|Content must be presented in a way that users can perceive it (e.g., text alternatives for images, captions for videos).|
|**O**perable|Users must be able to interact with the website (e.g., keyboard navigation, avoiding time limits).|
|**U**nderstandable|Content must be easy to read and navigate (e.g., clear labels, readable fonts).|
|**R**obust|Website should work across different devices, browsers, and assistive technologies.|

---

## **2️⃣ WCAG Versions & Levels**

WCAG has multiple versions and levels of compliance:

### **🔹 Versions**

- **WCAG 2.0** (2008) – The first widely adopted version.
    
- **WCAG 2.1** (2018) – Added improvements for mobile accessibility & cognitive disabilities.
    
- **WCAG 2.2** (2023) – Further improvements for keyboard users and low vision users.
    

### **🔹 Compliance Levels**

|Level|Description|
|---|---|
|**A (Basic)**|Minimum accessibility requirements (e.g., text alternatives for images).|
|**AA (Recommended)**|Higher accessibility (e.g., sufficient color contrast, keyboard-friendly navigation).|
|**AAA (Advanced)**|Best practices for accessibility, but often difficult to achieve fully.|

📌 **Most organizations aim for WCAG 2.1 Level AA compliance.**

---

## **3️⃣ Key WCAG Guidelines & Implementation**

### **🔹 1. Perceivable** (Making content visible & understandable)

✅ **Provide Text Alternatives (Alt Text) for Images**

- Screen readers need **descriptive alt text** for images.
    

html
<img src="logo.png" alt="Company logo - XYZ Corp">

✅ **Ensure Sufficient Color Contrast**

- Contrast between text and background should be **at least 4.5:1** (AA).
    
- Use tools like Contrast Checker to test colors.
    

✅ **Provide Captions & Transcripts for Audio/Video**
<video controls>
  <track src="subtitles.vtt" kind="subtitles" srclang="en" label="English">
</video>

✅ **Use Semantic HTML for Structure**

- Proper heading order (`h1 → h2 → h3`) helps screen readers.
<h1>Main Title</h1>
<h2>Subsection</h2>
<h3>Details</h3>
### **🔹 2. Operable** (Making content easy to navigate & interact with)

✅ **Keyboard Navigation Support**

- Users should navigate using the `Tab` key (no mouse needed).
    
- **Avoid keyboard traps** (elements users can’t navigate away from).
<button tabindex="0">Clickable Button</button>

✅ **Ensure Focus Visibility**

- Add a **visible focus indicator** for interactive elements.
button:focus {
  outline: 2px solid blue;
}

✅ **Avoid Automatic Content Changes**

- Don’t auto-play videos or refresh pages without user control.
    
- Allow users to **pause, stop, or hide** moving content.
    

✅ **Provide Skip Links** (Jump past repeated navigation)
<a href="#main-content" class="skip-link">Skip to main content</a>

### **🔹 3. Understandable** (Content should be easy to read and predict)

✅ **Use Simple Language**

- Avoid jargon and complex sentences.
    
- Use **plain language** tools like [Hemingway Editor](https://hemingwayapp.com/).
    

✅ **Provide Clear Labels & Instructions

<label for="email">Enter your email:</label>
<input type="email" id="email" placeholder="example@email.com">

✅ **Consistent Navigation & Predictable Behavior**

- **Menus, buttons, and layouts should be uniform** across pages.
    
- **Forms should provide error messages & suggestions**.
<input type="password" aria-describedby="password-hint">
<small id="password-hint">Use at least 8 characters.</small>

### **🔹 4. Robust** (Ensuring compatibility with different technologies)

✅ **Use ARIA (Accessible Rich Internet Applications) Where Needed**

- Adds accessibility for **dynamic content** like modals & alerts

<button aria-label="Close" aria-expanded="false">X</button>


✅ **Ensure Compatibility with Assistive Technologies**

- Test with screen readers like **NVDA, JAWS, or VoiceOver**.
    
- Use browser dev tools (`Lighthouse`, `axe DevTools`) for automated accessibility testing.
    

---

## **4️⃣ WCAG Interview Questions & Answers**

### **1. What is WCAG and why is it important?**

**Answer**:  
WCAG (Web Content Accessibility Guidelines) ensures that web content is **accessible to all users**, including those with disabilities. It improves **usability, compliance with legal requirements, and SEO**.

---

### **2. What are the 4 main principles of WCAG?**

**Answer**:  
WCAG follows the **POUR** principles:

1. **Perceivable** – Content should be visible & understandable.
    
2. **Operable** – Users must interact using keyboard/mouse.
    
3. **Understandable** – Content should be readable & predictable.
    
4. **Robust** – Works across devices and assistive tools.
    

---

### **3. What is the difference between WCAG 2.0 and WCAG 2.1?**

**Answer**:

- **WCAG 2.1** introduced new criteria for **mobile accessibility**, **low vision users**, and **cognitive impairments**.
    
- Added features like **keyboard shortcuts, text spacing, motion actuation**.
    

---

### **4. How do you test a website for accessibility?**

**Answer**:  
✅ Use **Lighthouse (Chrome DevTools)** for automatic audits.  
✅ Test with screen readers like **NVDA, JAWS, VoiceOver**.  
✅ Check keyboard navigation (`Tab`, `Enter`, `Space`).  
✅ Validate **color contrast** with tools like WebAIM.

---

### **5. How do you make a form accessible?**

**Answer**:

- Use **label elements** connected to input fields.
    
- Provide **aria-describedby** for hints.
    
- Use **semantic HTML** for structure.
<label for="name">Full Name:</label>
<input type="text" id="name" required>
