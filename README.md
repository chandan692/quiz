<html lang="en">
 <head>
  <meta charset="utf-8"/>
  <meta content="width=device-width, initial-scale=1" name="viewport"/>
  <title>
   Quiz Game
  </title>
  <script src="https://cdn.tailwindcss.com">
  </script>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" rel="stylesheet"/>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&amp;display=swap" rel="stylesheet"/>
  <style>
   body {
      font-family: 'Inter', sans-serif;
    }
  </style>
 </head>
 <body class="bg-gray-50 min-h-screen flex flex-col">
  <header class="bg-indigo-600 text-white p-4 shadow-md">
   <div class="container mx-auto flex justify-between items-center">
    <h1 class="text-2xl font-semibold flex items-center">
     <i class="fas fa-question-circle mr-2">
     </i>
     Quiz Game
    </h1>
    <nav class="space-x-4 text-indigo-200 hidden sm:flex">
     <button class="hover:text-white focus:outline-none focus:text-white" id="btn-categories">
      Categories
     </button>
     <button class="hover:text-white focus:outline-none focus:text-white" disabled="" id="btn-review">
      Review Answers
     </button>
     <button class="hover:text-white focus:outline-none focus:text-white" id="btn-reset">
      Reset Quiz
     </button>
    </nav>
    <button class="sm:hidden focus:outline-none" id="btn-menu">
     <i class="fas fa-bars text-white text-2xl">
     </i>
    </button>
   </div>
   <div class="hidden bg-indigo-700 text-indigo-200 p-2 space-y-2 sm:hidden" id="mobile-menu">
    <button class="block w-full text-left hover:text-white focus:outline-none focus:text-white" id="btn-categories-mobile">
     Categories
    </button>
    <button class="block w-full text-left hover:text-white focus:outline-none focus:text-white" disabled="" id="btn-review-mobile">
     Review Answers
    </button>
    <button class="block w-full text-left hover:text-none focus:outline-none focus:text-white" id="btn-reset-mobile">
     Reset Quiz
    </button>
   </div>
  </header>
  <main class="flex-grow container mx-auto p-4 max-w-3xl">
   <section class="mb-8" id="category-selection">
    <h2 class="text-xl font-semibold mb-4 text-indigo-700">
     Select a Category
    </h2>
    <div class="grid grid-cols-2 sm:grid-cols-3 gap-4">
     <button class="category-btn bg-indigo-100 hover:bg-indigo-200 text-indigo-800 rounded-lg p-4 font-medium shadow focus:outline-none focus:ring-2 focus:ring-indigo-500" data-category="General Knowledge">
      <img alt="Icon of a globe representing General Knowledge category" class="mx-auto mb-2" height="80" src="https://storage.googleapis.com/a1aa/image/93be3d95-cb78-4934-a775-38a0c9c7402b.jpg" width="80"/>
      General Knowledge
     </button>
     <button class="category-btn bg-indigo-100 hover:bg-indigo-200 text-indigo-800 rounded-lg p-4 font-medium shadow focus:outline-none focus:ring-2 focus:ring-indigo-500" data-category="Science">
      <img alt="Icon of an atom representing Science category" class="mx-auto mb-2" height="80" src="https://storage.googleapis.com/a1aa/image/1fb2cd13-9b9a-4fc0-ca0b-304fc153d065.jpg" width="80"/>
      Science
     </button>
     <button class="category-btn bg-indigo-100 hover:bg-indigo-200 text-indigo-800 rounded-lg p-4 font-medium shadow focus:outline-none focus:ring-2 focus:ring-indigo-500" data-category="History">
      <img alt="Icon of a historical monument representing History category" class="mx-auto mb-2" height="80" src="https://storage.googleapis.com/a1aa/image/aa1adb11-3d9a-44e3-e53a-df9a9fd9cd4a.jpg" width="80"/>
      History
     </button>
     <button class="category-btn bg-indigo-100 hover:bg-indigo-200 text-indigo-800 rounded-lg p-4 font-medium shadow focus:outline-none focus:ring-2 focus:ring-indigo-500" data-category="Sports">
      <img alt="Icon of a soccer ball representing Sports category" class="mx-auto mb-2" height="80" src="https://storage.googleapis.com/a1aa/image/9f8876f5-2ad8-4424-6aef-ff5eb19d94d9.jpg" width="80"/>
      Sports
     </button>
     <button class="category-btn bg-indigo-100 hover:bg-indigo-200 text-indigo-800 rounded-lg p-4 font-medium shadow focus:outline-none focus:ring-2 focus:ring-indigo-500" data-category="Movies">
      <img alt="Icon of a film reel representing Movies category" class="mx-auto mb-2" height="80" src="https://storage.googleapis.com/a1aa/image/5debf4d8-d843-4681-b5ac-af14176358f7.jpg" width="80"/>
      Movies
     </button>
     <button class="category-btn bg-indigo-100 hover:bg-indigo-200 text-indigo-800 rounded-lg p-4 font-medium shadow focus:outline-none focus:ring-2 focus:ring-indigo-500" data-category="Geography">
      <img alt="Icon of a map representing Geography category" class="mx-auto mb-2" height="80" src="https://storage.googleapis.com/a1aa/image/eba19c5a-6819-49f2-37ef-2c0b2299600d.jpg" width="80"/>
      Geography
     </button>
    </div>
   </section>
   <section class="hidden" id="quiz-section">
    <div class="flex justify-between items-center mb-4">
     <h2 class="text-xl font-semibold text-indigo-700" id="quiz-category">
     </h2>
     <div class="text-indigo-700 font-semibold">
      Question
      <span id="current-question-number">
       1
      </span>
      /
      <span id="total-questions">
       10
      </span>
     </div>
    </div>
    <div class="mb-6 text-lg font-medium text-gray-800" id="question-text">
    </div>
    <div class="grid gap-4" id="answers">
     <!-- Answer buttons inserted here dynamically -->
    </div>
    <div class="flex justify-between mt-6">
     <button class="bg-indigo-500 hover:bg-indigo-600 disabled:bg-indigo-300 text-white font-semibold py-2 px-4 rounded focus:outline-none focus:ring-2 focus:ring-indigo-400" disabled="" id="btn-prev">
      <i class="fas fa-arrow-left mr-2">
      </i>
      Previous
     </button>
     <button class="bg-indigo-500 hover:bg-indigo-600 disabled:bg-indigo-300 text-white font-semibold py-2 px-4 rounded focus:outline-none focus:ring-2 focus:ring-indigo-400" id="btn-next">
      Next
      <i class="fas fa-arrow-right ml-2">
      </i>
     </button>
    </div>
    <div class="mt-6 text-right text-gray-600 italic" id="timer-container">
     Time left:
     <span id="timer">
      30
     </span>
     seconds
    </div>
   </section>
   <section class="hidden text-center p-6 bg-white rounded-lg shadow-md" id="result-section">
    <h2 class="text-2xl font-bold text-indigo-700 mb-4">
     Quiz Completed!
    </h2>
    <p class="text-lg mb-6" id="score-text">
    </p>
    <button class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-2 px-6 rounded focus:outline-none focus:ring-2 focus:ring-indigo-400 mb-4" id="btn-review-answers">
     Review Answers
    </button>
    <button class="bg-green-600 hover:bg-green-700 text-white font-semibold py-2 px-6 rounded focus:outline-none focus:ring-2 focus:ring-green-400" id="btn-play-again">
     Play Again
    </button>
   </section>
   <section class="hidden max-h-[60vh] overflow-y-auto p-4 bg-white rounded-lg shadow-md" id="review-section">
    <h2 class="text-xl font-semibold text-indigo-700 mb-4">
     Review Your Answers
    </h2>
    <div class="space-y-6" id="review-list">
     <!-- Review items inserted here dynamically -->
    </div>
    <div class="mt-6 text-center">
     <button class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-2 px-6 rounded focus:outline-none focus:ring-2 focus:ring-indigo-400" id="btn-close-review">
      Close Review
     </button>
    </div>
   </section>
  </main>
  <footer class="bg-indigo-600 text-indigo-200 p-4 text-center text-sm">
   © 2024 Quiz Game. All rights reserved.
  </footer>
  <script>
   // Quiz data for categories with 10 questions each
    const quizData = {
      "General Knowledge": [
        {
          question: "What is the capital city of France?",
          answers: ["Paris", "London", "Berlin", "Madrid"],
          correct: 0,
          explanation: "Paris is the capital and most populous city of France."
        },
        {
          question: "Which planet is known as the Red Planet?",
          answers: ["Venus", "Mars", "Jupiter", "Saturn"],
          correct: 1,
          explanation: "Mars is often called the 'Red Planet' because of its reddish appearance."
        },
        {
          question: "What is the largest ocean on Earth?",
          answers: ["Atlantic Ocean", "Indian Ocean", "Arctic Ocean", "Pacific Ocean"],
          correct: 3,
          explanation: "The Pacific Ocean is the largest and deepest ocean on Earth."
        },
        {
          question: "Who wrote the play 'Romeo and Juliet'?",
          answers: ["William Shakespeare", "Charles Dickens", "Mark Twain", "Jane Austen"],
          correct: 0,
          explanation: "'Romeo and Juliet' is a tragedy written by William Shakespeare."
        },
        {
          question: "What is the chemical symbol for gold?",
          answers: ["Au", "Ag", "Gd", "Go"],
          correct: 0,
          explanation: "The chemical symbol for gold is Au."
        },
        {
          question: "Which country hosted the 2016 Summer Olympics?",
          answers: ["China", "Brazil", "UK", "Russia"],
          correct: 1,
          explanation: "Brazil hosted the 2016 Summer Olympics in Rio de Janeiro."
        },
        {
          question: "What is the tallest mountain in the world?",
          answers: ["K2", "Mount Everest", "Kangchenjunga", "Lhotse"],
          correct: 1,
          explanation: "Mount Everest is the tallest mountain above sea level."
        },
        {
          question: "Which language has the most native speakers worldwide?",
          answers: ["English", "Mandarin Chinese", "Spanish", "Hindi"],
          correct: 1,
          explanation: "Mandarin Chinese has the highest number of native speakers."
        },
        {
          question: "What is the currency of Japan?",
          answers: ["Yen", "Won", "Dollar", "Euro"],
          correct: 0,
          explanation: "The currency of Japan is the Yen."
        },
        {
          question: "Who painted the Mona Lisa?",
          answers: ["Leonardo da Vinci", "Vincent van Gogh", "Pablo Picasso", "Michelangelo"],
          correct: 0,
          explanation: "The Mona Lisa was painted by Leonardo da Vinci."
        }
      ],
      Science: [
        {
          question: "What is the chemical formula for water?",
          answers: ["H2O", "CO2", "NaCl", "O2"],
          correct: 0,
          explanation: "Water's chemical formula is H2O."
        },
        {
          question: "What gas do plants absorb from the atmosphere?",
          answers: ["Oxygen", "Nitrogen", "Carbon Dioxide", "Hydrogen"],
          correct: 2,
          explanation: "Plants absorb carbon dioxide for photosynthesis."
        },
        {
          question: "What is the speed of light?",
          answers: ["300,000 km/s", "150,000 km/s", "1,000 km/s", "30,000 km/s"],
          correct: 0,
          explanation: "The speed of light is approximately 300,000 kilometers per second."
        },
        {
          question: "Who developed the theory of relativity?",
          answers: ["Isaac Newton", "Albert Einstein", "Nikola Tesla", "Galileo Galilei"],
          correct: 1,
          explanation: "Albert Einstein developed the theory of relativity."
        },
        {
          question: "What part of the cell contains genetic material?",
          answers: ["Cytoplasm", "Nucleus", "Mitochondria", "Ribosome"],
          correct: 1,
          explanation: "The nucleus contains the cell's genetic material."
        },
        {
          question: "What is the main gas found in the Earth's atmosphere?",
          answers: ["Oxygen", "Nitrogen", "Carbon Dioxide", "Argon"],
          correct: 1,
          explanation: "Nitrogen makes up about 78% of Earth's atmosphere."
        },
        {
          question: "What is the process by which plants make food?",
          answers: ["Respiration", "Photosynthesis", "Transpiration", "Fermentation"],
          correct: 1,
          explanation: "Photosynthesis is the process plants use to make food."
        },
        {
          question: "What is the unit of electrical resistance?",
          answers: ["Volt", "Ohm", "Ampere", "Watt"],
          correct: 1,
          explanation: "The unit of electrical resistance is the Ohm."
        },
        {
          question: "Which organ in the human body produces insulin?",
          answers: ["Liver", "Pancreas", "Kidney", "Heart"],
          correct: 1,
          explanation: "The pancreas produces insulin."
        },
        {
          question: "What type of energy is stored in a stretched spring?",
          answers: ["Kinetic Energy", "Thermal Energy", "Potential Energy", "Chemical Energy"],
          correct: 2,
          explanation: "A stretched spring stores potential energy."
        }
      ],
      History: [
        {
          question: "Who was the first President of the United States?",
          answers: ["George Washington", "Thomas Jefferson", "Abraham Lincoln", "John Adams"],
          correct: 0,
          explanation: "George Washington was the first U.S. President."
        },
        {
          question: "In which year did World War II end?",
          answers: ["1945", "1939", "1918", "1963"],
          correct: 0,
          explanation: "World War II ended in 1945."
        },
        {
          question: "Which ancient civilization built the pyramids?",
          answers: ["Romans", "Greeks", "Egyptians", "Mayans"],
          correct: 2,
          explanation: "The Egyptians built the pyramids."
        },
        {
          question: "Who was known as the Maid of Orléans?",
          answers: ["Joan of Arc", "Cleopatra", "Queen Elizabeth I", "Marie Curie"],
          correct: 0,
          explanation: "Joan of Arc was called the Maid of Orléans."
        },
        {
          question: "What was the name of the ship on which the Pilgrims traveled to America?",
          answers: ["Mayflower", "Santa Maria", "Endeavour", "Beagle"],
          correct: 0,
          explanation: "The Pilgrims traveled on the Mayflower."
        },
        {
          question: "Who was the British Prime Minister during most of World War II?",
          answers: ["Winston Churchill", "Neville Chamberlain", "Clement Attlee", "Margaret Thatcher"],
          correct: 0,
          explanation: "Winston Churchill was the British Prime Minister during most of WWII."
        },
        {
          question: "Which empire was ruled by Genghis Khan?",
          answers: ["Roman Empire", "Mongol Empire", "Ottoman Empire", "Persian Empire"],
          correct: 1,
          explanation: "Genghis Khan ruled the Mongol Empire."
        },
        {
          question: "What wall divided East and West Berlin?",
          answers: ["Great Wall of China", "Berlin Wall", "Hadrian's Wall", "Wailing Wall"],
          correct: 1,
          explanation: "The Berlin Wall divided East and West Berlin."
        },
        {
          question: "Who discovered America in 1492?",
          answers: ["Christopher Columbus", "Vasco da Gama", "Ferdinand Magellan", "Marco Polo"],
          correct: 0,
          explanation: "Christopher Columbus is credited with discovering America in 1492."
        },
        {
          question: "What was the Renaissance?",
          answers: ["A war", "A cultural movement", "A disease", "A political party"],
          correct: 1,
          explanation: "The Renaissance was a cultural movement that revived art and learning."
        }
      ],
      Sports: [
        {
          question: "How many players are on a soccer team on the field?",
          answers: ["9", "10", "11", "12"],
          correct: 2,
          explanation: "There are 11 players on a soccer team on the field."
        },
        {
          question: "Which country won the FIFA World Cup in 2018?",
          answers: ["Brazil", "Germany", "France", "Argentina"],
          correct: 2,
          explanation: "France won the 2018 FIFA World Cup."
        },
        {
          question: "In which sport is the term 'home run' used?",
          answers: ["Cricket", "Baseball", "Tennis", "Basketball"],
          correct: 1,
          explanation: "'Home run' is a term used in baseball."
        },
        {
          question: "How many rings are on the Olympic flag?",
          answers: ["4", "5", "6", "7"],
          correct: 1,
          explanation: "The Olympic flag has 5 interlocking rings."
        },
        {
          question: "Which sport uses a shuttlecock?",
          answers: ["Tennis", "Badminton", "Squash", "Table Tennis"],
          correct: 1,
          explanation: "Badminton uses a shuttlecock."
        },
        {
          question: "Who holds the record for most goals in World Cup history?",
          answers: ["Pelé", "Miroslav Klose", "Ronaldo", "Lionel Messi"],
          correct: 1,
          explanation: "Miroslav Klose holds the record for most World Cup goals."
        },
        {
          question: "What is the length of an Olympic swimming pool?",
          answers: ["25 meters", "50 meters", "100 meters", "75 meters"],
          correct: 1,
          explanation: "An Olympic swimming pool is 50 meters long."
        },
        {
          question: "Which country invented the sport of golf?",
          answers: ["USA", "Scotland", "England", "Ireland"],
          correct: 1,
          explanation: "Golf originated in Scotland."
        },
        {
          question: "In which sport do players score points by throwing a ball through a hoop?",
          answers: ["Volleyball", "Basketball", "Handball", "Water Polo"],
          correct: 1,
          explanation: "Basketball players score by throwing the ball through a hoop."
        },
        {
          question: "What is the maximum score in a single frame of bowling?",
          answers: ["10", "20", "30", "40"],
          correct: 2,
          explanation: "The maximum score in a single frame is 30 (a strike followed by two strikes)."
        }
      ],
      Movies: [
        {
          question: "Who directed the movie 'Jurassic Park'?",
          answers: ["Steven Spielberg", "James Cameron", "Christopher Nolan", "Martin Scorsese"],
          correct: 0,
          explanation: "'Jurassic Park' was directed by Steven Spielberg."
        },
        {
          question: "Which movie features the character 'Forrest Gump'?",
          answers: ["Cast Away", "Forrest Gump", "The Green Mile", "Saving Private Ryan"],
          correct: 1,
          explanation: "'Forrest Gump' is the title character of the movie."
        },
        {
          question: "What is the highest-grossing film of all time (as of 2024)?",
          answers: ["Avatar", "Avengers: Endgame", "Titanic", "Star Wars: The Force Awakens"],
          correct: 0,
          explanation: "'Avatar' is the highest-grossing film of all time."
        },
        {
          question: "Which actor played Jack Sparrow in 'Pirates of the Caribbean'?",
          answers: ["Johnny Depp", "Orlando Bloom", "Leonardo DiCaprio", "Brad Pitt"],
          correct: 0,
          explanation: "Johnny Depp played Captain Jack Sparrow."
        },
        {
          question: "In which movie series does the character 'Darth Vader' appear?",
          answers: ["Star Trek", "Star Wars", "The Matrix", "Harry Potter"],
          correct: 1,
          explanation: "'Darth Vader' is a character in Star Wars."
        },
        {
          question: "Which movie won the Academy Award for Best Picture in 2020?",
          answers: ["1917", "Parasite", "Joker", "Once Upon a Time in Hollywood"],
          correct: 1,
          explanation: "'Parasite' won Best Picture in 2020."
        },
        {
          question: "Who played the female lead in the movie 'Titanic'?",
          answers: ["Kate Winslet", "Natalie Portman", "Scarlett Johansson", "Jennifer Lawrence"],
          correct: 0,
          explanation: "Kate Winslet played Rose in 'Titanic'."
        },
        {
          question: "What genre is the movie 'Inception'?",
          answers: ["Romantic Comedy", "Science Fiction", "Horror", "Documentary"],
          correct: 1,
          explanation: "'Inception' is a science fiction thriller."
        },
        {
          question: "Which movie features the song 'My Heart Will Go On'?",
          answers: ["The Bodyguard", "Titanic", "Frozen", "Moulin Rouge"],
          correct: 1,
          explanation: "The song is from the movie 'Titanic'."
        },
        {
          question: "Who is the creator of the 'Harry Potter' film series?",
          answers: ["J.K. Rowling", "Steven Spielberg", "David Yates", "Chris Columbus"],
          correct: 0,
          explanation: "J.K. Rowling wrote the Harry Potter books; David Yates directed most films."
        }
      ],
      Geography: [
        {
          question: "What is the longest river in the world?",
          answers: ["Amazon", "Nile", "Yangtze", "Mississippi"],
          correct: 1,
          explanation: "The Nile is considered the longest river in the world."
        },
        {
          question: "Which country has the largest land area?",
          answers: ["Canada", "China", "Russia", "USA"],
          correct: 2,
          explanation: "Russia has the largest land area."
        },
        {
          question: "Mount Kilimanjaro is located in which country?",
          answers: ["Kenya", "Tanzania", "Uganda", "Ethiopia"],
          correct: 1,
          explanation: "Mount Kilimanjaro is in Tanzania."
        },
        {
          question: "What is the capital of Australia?",
          answers: ["Sydney", "Melbourne", "Canberra", "Brisbane"],
          correct: 2,
          explanation: "Canberra is the capital of Australia."
        },
        {
          question: "Which desert is the largest in the world?",
          answers: ["Sahara", "Gobi", "Kalahari", "Antarctic Desert"],
          correct: 3,
          explanation: "The Antarctic Desert is the largest desert by area."
        },
        {
          question: "Which ocean is Bermuda located in?",
          answers: ["Atlantic Ocean", "Pacific Ocean", "Indian Ocean", "Arctic Ocean"],
          correct: 0,
          explanation: "Bermuda is located in the Atlantic Ocean."
        },
        {
          question: "Which country is known as the Land of the Rising Sun?",
          answers: ["China", "Japan", "South Korea", "Thailand"],
          correct: 1,
          explanation: "Japan is known as the Land of the Rising Sun."
        },
        {
          question: "What is the smallest country in the world?",
          answers: ["Monaco", "Vatican City", "Nauru", "San Marino"],
          correct: 1,
          explanation: "Vatican City is the smallest country."
        },
        {
          question: "Which continent is the Sahara Desert located on?",
          answers: ["Asia", "Africa", "Australia", "South America"],
          correct: 1,
          explanation: "The Sahara Desert is in Africa."
        },
        {
          question: "What is the capital city of Canada?",
          answers: ["Toronto", "Vancouver", "Ottawa", "Montreal"],
          correct: 2,
          explanation: "Ottawa is the capital of Canada."
        }
      ]
    };

    const totalQuestions = 10;
    let currentCategory = null;
    let currentQuestionIndex = 0;
    let userAnswers = [];
    let timerInterval = null;
    let timeLeft = 30;

    // DOM Elements
    const categorySelection = document.getElementById("category-selection");
    const quizSection = document.getElementById("quiz-section");
    const resultSection = document.getElementById("result-section");
    const reviewSection = document.getElementById("review-section");

    const quizCategoryTitle = document.getElementById("quiz-category");
    const currentQuestionNumber = document.getElementById("current-question-number");
    const totalQuestionsSpan = document.getElementById("total-questions");
    const questionText = document.getElementById("question-text");
    const answersContainer = document.getElementById("answers");
    const btnPrev = document.getElementById("btn-prev");
    const btnNext = document.getElementById("btn-next");
    const timerDisplay = document.getElementById("timer");
    const timerContainer = document.getElementById("timer-container");

    const scoreText = document.getElementById("score-text");
    const btnReviewAnswers = document.getElementById("btn-review-answers");
    const btnPlayAgain = document.getElementById("btn-play-again");

    const reviewList = document.getElementById("review-list");
    const btnCloseReview = document.getElementById("btn-close-review");

    const btnCategories = document.getElementById("btn-categories");
    const btnReview = document.getElementById("btn-review");
    const btnReset = document.getElementById("btn-reset");

    const btnCategoriesMobile = document.getElementById("btn-categories-mobile");
    const btnReviewMobile = document.getElementById("btn-review-mobile");
    const btnResetMobile = document.getElementById("btn-reset-mobile");

    const btnMenu = document.getElementById("btn-menu");
    const mobileMenu = document.getElementById("mobile-menu");

    // Toggle mobile menu
    btnMenu.addEventListener("click", () => {
      mobileMenu.classList.toggle("hidden");
    });

    // Category selection buttons
    document.querySelectorAll(".category-btn").forEach((btn) => {
      btn.addEventListener("click", () => {
        startQuiz(btn.dataset.category);
        if (!mobileMenu.classList.contains("hidden")) {
          mobileMenu.classList.add("hidden");
        }
      });
    });

    // Navigation buttons in header
    btnCategories.addEventListener("click", () => {
      showCategorySelection();
    });
    btnCategoriesMobile.addEventListener("click", () => {
      showCategorySelection();
      mobileMenu.classList.add("hidden");
    });

    btnReview.addEventListener("click", () => {
      if (!btnReview.disabled) showReview();
    });
    btnReviewMobile.addEventListener("click", () => {
      if (!btnReviewMobile.disabled) showReview();
      mobileMenu.classList.add("hidden");
    });

    btnReset.addEventListener("click", () => {
      resetQuiz();
    });
    btnResetMobile.addEventListener("click", () => {
      resetQuiz();
      mobileMenu.classList.add("hidden");
    });

    // Quiz navigation buttons
    btnPrev.addEventListener("click", () => {
      if (currentQuestionIndex > 0) {
        currentQuestionIndex--;
        showQuestion();
      }
    });

    btnNext.addEventListener("click", () => {
      if (currentQuestionIndex < totalQuestions - 1) {
        currentQuestionIndex++;
        showQuestion();
      } else {
        finishQuiz();
      }
    });

    // Result buttons
    btnReviewAnswers.addEventListener("click", () => {
      showReview();
    });

    btnPlayAgain.addEventListener("click", () => {
      showCategorySelection();
    });

    // Review close button
    btnCloseReview.addEventListener("click", () => {
      reviewSection.classList.add("hidden");
      resultSection.classList.remove("hidden");
    });

    // Start quiz with selected category
    function startQuiz(category) {
      currentCategory = category;
      currentQuestionIndex = 0;
      userAnswers = new Array(totalQuestions).fill(null);
      categorySelection.classList.add("hidden");
      resultSection.classList.add("hidden");
      reviewSection.classList.add("hidden");
      quizSection.classList.remove("hidden");
      btnReview.disabled = true;
      btnReviewMobile.disabled = true;
      quizCategoryTitle.textContent = category;
      totalQuestionsSpan.textContent = totalQuestions;
      showQuestion();
      startTimer();
    }

    // Show category selection screen
    function showCategorySelection() {
      currentCategory = null;
      currentQuestionIndex = 0;
      userAnswers = [];
      clearInterval(timerInterval);
      timerContainer.classList.add("hidden");
      quizSection.classList.add("hidden");
      resultSection.classList.add("hidden");
      reviewSection.classList.add("hidden");
      categorySelection.classList.remove("hidden");
      btnReview.disabled = true;
      btnReviewMobile.disabled = true;
    }

    // Show current question and answers
    function showQuestion() {
      clearInterval(timerInterval);
      timeLeft = 30;
      timerDisplay.textContent = timeLeft;
      timerContainer.classList.remove("hidden");
      startTimer();

      const questionObj = quizData[currentCategory][currentQuestionIndex];
      currentQuestionNumber.textContent = currentQuestionIndex + 1;
      questionText.textContent = questionObj.question;

      answersContainer.innerHTML = "";
      questionObj.answers.forEach((answer, index) => {
        const btn = document.createElement("button");
        btn.type = "button";
        btn.className =
          "text-left p-4 rounded-lg border border-indigo-300 hover:bg-indigo-100 focus:outline-none focus:ring-2 focus:ring-indigo-400 transition-colors";
        btn.textContent = answer;
        btn.dataset.index = index;
        if (userAnswers[currentQuestionIndex] === index) {
          btn.classList.add("bg-indigo-200", "border-indigo-600");
        }
        btn.addEventListener("click", () => {
          userAnswers[currentQuestionIndex] = index;
          updateAnswerSelection();
        });
        answersContainer.appendChild(btn);
      });

      btnPrev.disabled = currentQuestionIndex === 0;
      btnNext.textContent =
        currentQuestionIndex === totalQuestions - 1 ? "Finish" : "Next";
    }

    // Update answer button styles based on selection
    function updateAnswerSelection() {
      const buttons = answersContainer.querySelectorAll("button");
      buttons.forEach((btn) => {
        btn.classList.remove("bg-indigo-200", "border-indigo-600");
        if (
          userAnswers[currentQuestionIndex] !== null &&
          +btn.dataset.index === userAnswers[currentQuestionIndex]
        ) {
          btn.classList.add("bg-indigo-200", "border-indigo-600");
        }
      });
    }

    // Timer logic
    function startTimer() {
      clearInterval(timerInterval);
      timerInterval = setInterval(() => {
        timeLeft--;
        timerDisplay.textContent = timeLeft;
        if (timeLeft <= 0) {
          clearInterval(timerInterval);
          // Auto move to next question or finish
          if (userAnswers[currentQuestionIndex] === null) {
            userAnswers[currentQuestionIndex] = null; // unanswered
          }
          if (currentQuestionIndex < totalQuestions - 1) {
            currentQuestionIndex++;
            showQuestion();
          } else {
            finishQuiz();
          }
        }
      }, 1000);
    }

    // Finish quiz and show results
    function finishQuiz() {
      clearInterval(timerInterval);
      quizSection.classList.add("hidden");
      resultSection.classList.remove("hidden");
      timerContainer.classList.add("hidden");

      let score = 0;
      const questions = quizData[currentCategory];
      for (let i = 0; i < totalQuestions; i++) {
        if (userAnswers[i] === questions[i].correct) {
          score++;
        }
      }
      scoreText.textContent = `You scored ${score} out of ${totalQuestions}.`;
      btnReview.disabled = false;
      btnReviewMobile.disabled = false;
    }

    // Show review answers section
    function showReview() {
      reviewList.innerHTML = "";
      reviewSection.classList.remove("hidden");
      resultSection.classList.add("hidden");
      quizSection.classList.add("hidden");
      categorySelection.classList.add("hidden");

      const questions = quizData[currentCategory];
      for (let i = 0; i < totalQuestions; i++) {
        const q = questions[i];
        const userAnswerIndex = userAnswers[i];
        const isCorrect = userAnswerIndex === q.correct;

        const reviewItem = document.createElement("div");
        reviewItem.className =
          "p-4 border rounded-lg shadow-sm bg-gray-50";

        const questionEl = document.createElement("h3");
        questionEl.className = "font-semibold text-indigo-700 mb-2";
        questionEl.textContent = `Q${i + 1}: ${q.question}`;
        reviewItem.appendChild(questionEl);

        const userAnswerEl = document.createElement("p");
        userAnswerEl.className = isCorrect
          ? "text-green-700 font-semibold"
          : "text-red-700 font-semibold";
        userAnswerEl.textContent =
          userAnswerIndex === null
            ? "You did not answer this question."
            : `Your answer: ${q.answers[userAnswerIndex]}`;
        reviewItem.appendChild(userAnswerEl);

        if (!isCorrect) {
          const correctAnswerEl = document.createElement("p");
          correctAnswerEl.className = "text-green-700 font-semibold";
          correctAnswerEl.textContent = `Correct answer: ${q.answers[q.correct]}`;
          reviewItem.appendChild(correctAnswerEl);
        }

        if (q.explanation) {
          const explanationEl = document.createElement("p");
          explanationEl.className = "mt-2 text-gray-700 italic";
          explanationEl.textContent = `Explanation: ${q.explanation}`;
          reviewItem.appendChild(explanationEl);
        }

        reviewList.appendChild(reviewItem);
      }
    }

    // Reset quiz to initial state
    function resetQuiz() {
      clearInterval(timerInterval);
      currentCategory = null;
      currentQuestionIndex = 0;
      userAnswers = [];
      categorySelection.classList.remove("hidden");
      quizSection.classList.add("hidden");
      resultSection.classList.add("hidden");
      reviewSection.classList.add("hidden");
      timerContainer.classList.add("hidden");
      btnReview.disabled = true;
      btnReviewMobile.disabled = true;
    }

    // Initialize app
    showCategorySelection();
  </script>
 </body>
</html>
