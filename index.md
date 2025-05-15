# Code-Memo

#### Code Memo

Welcome to my [Code Memo](https://mouhamaddev.github.io/Code-Memo/)! I forget a lot! So I created this simple project, which is a collection of my notes on various programming topics, including Python, Django, Django REST Framework (DRF), algorithms and data structures (maybe some leetcode problems), and Linux. This serves as my personal reference to help me recall concepts quickly. I hope you find it useful as well.

## Table of Contents

1. [Python](/python.md)
2. [Data Structures and Algorithms](/dsa.md)
3. [Django and Django REST Framework (DRF)](/django.md)
4. [Software Engineering Principles](/sep.md)
5. System Design and Architecture ⏳
6. API Design ⏳
7. [DevOps and Deployment](/devops.md)
8. [Linux](/linux.md)
9. [Misc](/misc.md)
10. [Interview Preparation](/interviews.md)
11. [Today I Learned - DAF 🔥](https://github.com/mouhamaddev/django-async-framework/tree/today-i-learned/TIL)

<p>
  <a href="#" onclick="randomPage();" style="text-decoration:none;">
    <button style="padding:10px 15px; font-size:14px; color:white; background-color:#007BFF; border:none; border-radius:5px; cursor:pointer;">
      Take Me to a Random Page &nbsp; 🎲
    </button>
  </a>
</p>

<script>
  async function randomPage() {
    try {
      const response = await fetch('pages.json');
      const data = await response.json();
      
      if (data.pages.length > 0) {
        let randomPage = data.pages[Math.floor(Math.random() * data.pages.length)];
        
        randomPage = randomPage.replace(/\.md$/, '');

        window.location.href = randomPage;
      } else {
        console.error("No pages found");
      }
    } catch (error) {
      console.error("Error fetching pages:", error);
    }
  }
</script>

<br>

Note: This project is a bunch of personal notes. While you may find them useful, it's intended more as a quick reference rather than a learning resource, ideal for a brief review 5 minutes before your next interview :D

Feel free to explore each section and make use of the information as needed. If you have any suggestions or contributions, please don't hesitate to create a pull request or open an issue.

And don't forget to take notes! ❤️

Version: 3.0.1
