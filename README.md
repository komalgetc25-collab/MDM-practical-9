<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>My To-Do List</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-gray-100">

    <div class="max-w-md mx-auto mt-10 bg-white p-6 rounded-lg shadow-lg">

        <h1 class="text-3xl font-bold text-center text-blue-600 mb-6">
            My To-Do List
        </h1>

        <!-- Input -->
        <div class="flex gap-2">

            <input
                type="text"
                id="taskInput"
                placeholder="Enter a task..."
                class="flex-1 border border-gray-300 p-2 rounded"
            >

            <button
                id="addButton"
                class="bg-blue-600 text-white px-4 py-2 rounded
                       hover:bg-blue-700"
            >
                Add
            </button>

        </div>

        <!-- Task List -->
        <ul id="taskList" class="mt-6 space-y-3"></ul>

    </div>


    <script>

        // Get elements
        const taskInput = document.getElementById("taskInput");
        const addButton = document.getElementById("addButton");
        const taskList = document.getElementById("taskList");


        // Add task
        addButton.addEventListener("click", function () {

            let taskText = taskInput.value.trim();

            if (taskText === "") {
                alert("Please enter a task!");
                return;
            }

            // Create list item
            let li = document.createElement("li");

            li.className =
                "flex items-center justify-between bg-gray-100 p-3 rounded";


            // Task text
            let span = document.createElement("span");

            span.innerText = taskText;

            span.className = "cursor-pointer";


            // Complete task
            span.addEventListener("click", function () {

                span.classList.toggle("line-through");
                span.classList.toggle("text-gray-400");

            });


            // Delete button
            let deleteButton = document.createElement("button");

            deleteButton.innerText = "Delete";

            deleteButton.className =
                "bg-red-500 text-white px-3 py-1 rounded hover:bg-red-600";


            // Delete task
            deleteButton.addEventListener("click", function () {

                li.remove();

            });


            // Add elements
            li.appendChild(span);
            li.appendChild(deleteButton);

            taskList.appendChild(li);

            // Clear input
            taskInput.value = "";

        });


        // Add task using Enter key
        taskInput.addEventListener("keypress", function (event) {

            if (event.key === "Enter") {
                addButton.click();
            }

        });

    </script>

</body>
</html>
