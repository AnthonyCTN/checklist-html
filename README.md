# checklist-html
checklist html css javascript


</head>
<body>
    <nav>
        <ul>
            <li><a href="application.html">Accueil</a></li>
            <li><a href="asitepresentation.html">Exercice</a></li>
        </ul>
    </nav>
    <div id="container">
        <h1>Ma Checklist</h1>
        <div id="checklist-container">
        </div>
        <div id="add-item">
            <input type="text" id="new-item" placeholder="Nouvelle tâche...">
            <button id="add-button" onclick="addItem()">Ajouter</button>
        </div>
    </div>

    <script>
        function toggleChecked(itemId) {
            const item = document.getElementById(itemId);
            const itemLabel = document.querySelector(`label[for="${itemId}"]`);
            
            if (item.checked) {
                itemLabel.parentElement.classList.add("checked");
            } else {
                itemLabel.parentElement.classList.remove("checked");
            }
        }
    
        function addItem() {
            const newItemText = document.getElementById("new-item").value.trim();
            if (newItemText !== "") {
                const checklistContainer = document.getElementById("checklist-container");
                const newItemId = "item" + (checklistContainer.children.length + 1);
    
                const newChecklistItem = document.createElement("div");
                newChecklistItem.classList.add("checklist-item");
    
                const newCheckbox = document.createElement("input");
                newCheckbox.type = "checkbox";
                newCheckbox.id = newItemId;
                newCheckbox.onchange = function() {
                    toggleChecked(newItemId);
                };
    
                const newLabel = document.createElement("label");
                newLabel.htmlFor = newItemId;
                newLabel.textContent = newItemText;
    
                newChecklistItem.appendChild(newCheckbox);
                newChecklistItem.appendChild(newLabel);
    
                checklistContainer.appendChild(newChecklistItem);
    
                document.getElementById("new-item").value = ""; // Reset the input field
            }
        }
    </script>
</body>
</html>


<style>
         body {
            font-family: Arial, sans-serif;
            background-color: #292f3f;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        #container {
            width: 90%;
            max-width: 600px;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }

        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 30px;
        }

        .checklist-item {
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }

        .checklist-item input[type="checkbox"] {
            margin-right: 10px;
        }

        .checklist-item label {
            font-size: 18px;
            color: #555;
            flex: 1;
        }

        .checked label {
            text-decoration: line-through;
            color: #888;
        }

        #add-item {
            display: flex;
            align-items: center;
            border-top: 1px solid #ccc;
            padding-top: 10px;
            margin-top: 20px;
        }

        #new-item {
            flex: 1;
            padding: 8px;
            font-size: 16px;
            border: none;
            border-bottom: 2px solid #070707;
            outline: none;
        }

        #add-button {
            padding: 10px 15px;
            background-color: #000000;
            color: #fff;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        #add-button:hover {
            background-color:#007bff;
        }

        /* Responsive styles for mobile */
        @media screen and (max-width: 480px) {
            #container {
                width: 95%;
            }

            h1 {
                font-size: 24px;
            }

            .checklist-item label {
                font-size: 16px;
            }

            #new-item {
                font-size: 14px;
            }
        }


    nav {
        background-color: #292f3f;
        padding: 10px;
        position: absolute;
        top: 10px;
        left: 10px;
        right: 10px;
        display: flex;
        justify-content: center;
        z-index: 1;
    }

    nav ul {
        list-style-type: none;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
    }

    nav li {
        margin: 0 10px;
    }

    nav a {
        color: #fff;
        text-decoration: none;
        font-size: 18px;
    }

    nav a:hover {
        color: #007bff;
    }

    
  </style>

