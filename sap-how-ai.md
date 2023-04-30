---
title: SAP.how AI
permalink: /sap-how-ai
---

<h1>SAP.how AI</h1>

<script>
    
    document.addEventListener("DOMContentLoaded", function() {
        document.getElementById("question-form").addEventListener("submit", async function(event) {
            event.preventDefault();
            
            // Show the spinner
            document.getElementById("loading-spinner").style.display = "inline-block";

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
                    // Hide the spinner
                    document.getElementById("loading-spinner").style.display = "none";
                } else {
                    throw new Error(`HTTP error: ${response.status}`);
                }
            } catch (error) {
                console.error("Error:", error);
                document.getElementById("answer").textContent = "An error occurred. Possibly OpenAI usage limit is reached. Please try later.";
                // Hide the spinner
                document.getElementById("loading-spinner").style.display = "none";
            }
        });
    });
</script>

<p>SAP.how AI is a GPT-3.5-based machine learning model that has been fine-tuned using high-quality SAP-related data. We used the OpenAI API to optimize the model's effectiveness for answering questions about SAP products, particularly those related to SAP EWM functionality. Knowledge about other SAP systems will be delivered in future. While the model doesn't know everything, it should be able to provide helpful insights for SAP consulting.</p>

<p>At present, users can access the model for free, but there is a monthly usage limit. Once the limit is reached, the model will become unavailable until the next month.</p>

<p>
    <form id="question-form">
        <label for="question"><strong>Ask a question:</strong></label>
        <input type="text" id="question" name="question" required>
        <button id="submit-btn" type="submit">Submit</button>
        <span id="loading-spinner" class="spinner" style="display: none;"></span>
    </form>
</p>

<h2>Answer</h2>

<p id="answer"></p>
