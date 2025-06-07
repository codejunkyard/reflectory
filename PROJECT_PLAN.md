# **Project Plan: Insight - Article Analysis Service**

## **Overview**
Insight is an AI-driven service integrated into the **Reflectory** project. Its purpose is to analyze articles for authenticity, bias, source reliability, and other characteristics. Insight will allow users to easily access article evaluations via an Android interface, providing real-time feedback and insights.

---

## **1. Article Extraction**
### **Methods of Extraction**
- **Share Feature**: Allow users to share articles directly to the app for analysis. The app will extract the article content from the shared link.  
- **WebView Extraction**: Integrate a WebView to load articles, from which the app will extract relevant content for analysis.
- **Direct TextView Extraction**: For already existing articles in TextView format, implement extraction methods to parse the content and send it for analysis.  

### **Extraction Process**
- **HTML Parsing**: Use libraries like [Jsoup](https://jsoup.org/) to extract article bodies from HTML content.  
- **TextView Parsing**: For content within a TextView, extract plain text and format it for submission to Insight’s analysis system.  

---

## **2. Android UI - Floating Bubble**
### **UI Concept**
- **Floating Bubble Icon**:  
  - The bubble will float over all apps, always accessible to the user.
  - It will display the **Insight Icon**.
  - The bubble will show different colors based on the analysis status:  
    - **Gray (Not Started)** – Analysis has not begun.  
    - **Blue (Running)** – The analysis is in progress.  
    - **Green (Completed)** – Analysis has been completed.  
  - A **numeric score** will also be displayed on the bubble, reflecting the analysis process.

### **User Interaction**
- **Click Action**:  
  - Tapping the bubble will expand it to reveal further details of the analysis.
  - **Expanded View**:  
    - Show a breakdown of the **score spread** across different categories (e.g., Bias, Authenticity, Source, etc.).
    - Users can click on each category for more detailed analysis, e.g., identifying biases or issues related to that specific area.
  
---

## **3. Implementation Considerations**
### **No Accessibility API** (Preferred Option)
- Aim to implement the floating bubble using **standard Android UI techniques** such as **System Overlay** or **WindowManager** without the need for Accessibility API.
- **Challenges**: If the bubble needs to interact with content across apps, we may need to consider Accessibility features for seamless integration.

### **Fallback: Accessibility API**
- If it's not feasible to avoid the **Accessibility API**, ensure minimal usage. The Accessibility API will allow us to track content across apps and extract relevant information for analysis.
- **Usage**: Only utilize it to fetch content from TextViews across apps or identify articles on-screen for analysis.

---

## **4. Key Features and Milestones**
### **Feature List**
- **Article Extraction**: Implement extraction from shared links, WebView, and TextView.
- **UI Design**: Create the floating bubble with dynamic state changes (not started, in progress, completed).
- **AI Analysis**: Implement the core analysis logic to process articles and produce scores for credibility, bias, etc.
- **Score Display**: Visual representation of the analysis score with detailed category breakdowns.
- **Local & Remote Storage**: Store analysis results for reuse and minimize re-processing of identical articles.

### **Milestones**
1. **Article Extraction**: Implement extraction from WebView and TextView (Week 1-2).
2. **UI Bubble Design**: Create the floating bubble with the state-change functionality (Week 2-3).
3. **AI Analysis Engine**: Develop the core analysis functionality (Week 3-5).
4. **Final Integration**: Combine article extraction, UI bubble, and analysis engine. Test interactions and data flow (Week 5-6).

---

## **5. Future Enhancements**
- Integrate more advanced features such as **deepfake detection** and **scam recognition**.
- Extend the analysis to cover **image-based content**, detecting misleading images and headlines.
- Add support for **voice-to-text** inputs for hands-free analysis.

