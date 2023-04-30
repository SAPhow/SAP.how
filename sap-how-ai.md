---
title: SAP.how AI
permalink: /sap-how-ai
---

<h1>SAP.how AI</h1>

<script>
    
    document.addEventListener("DOMContentLoaded", function() {
        document.getElementById("question-form").addEventListener("submit", async function(event) {
            event.preventDefault();

            const question = document.getElementById("question").value;
            const url = "https://kh4rit.pythonanywhere.com/api/ask";
            const data = new FormData(event.target);

            try {
                const response = await fetch(url, {
                    method: "POST",
                    body: data
                });

                if (response.ok) {
                    const jsonResponse = await response.json();
                    document.getElementById("answer").textContent = jsonResponse.answer;
                } else {
                    throw new Error(`HTTP error: ${response.status}`);
                }
            } catch (error) {
                console.error("Error:", error);
                document.getElementById("answer").textContent = "An error occurred. Possibly OpenAI usage limit is reached. Please try later.";
            }
        });
    });
</script>

<p>
    <form id="question-form">
        <label for="question">Ask a question:</label>
        <input type="text" id="question" name="question" required>
        <button type="submit">Submit</button>
    </form>
</p>

<h2>Answer</h2>

<p id="answer"></p>
