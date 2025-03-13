
<h2  align="center" > 🕍 𝐐υ𝗂ƶ 𝐀ρρ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/b46675b4-e545-499f-913f-69def5ce20a7" width="" height=""/>

</h1>

</br>

```TS

//============ store/useQuizStore.ts ============== 

import { create } from "zustand";

type Question = {
  question: string;
  options: string[];
  correctAnswer: number;
};

interface QuizState {
  currentQuestion: number;
  answers: (number | null)[];
  score: number;
  showScore: boolean;
  questions: Question[];
  selectAnswer: (optionIndex: number) => void;
  nextQuestion: () => void;
  prevQuestion: () => void;
  resetQuiz: () => void;
}

const useQuizStore = create<QuizState>((set) => ({
  currentQuestion: 0,
  answers: Array(3).fill(null),
  score: 0,
  showScore: false,

  questions: [
    {
      question: "What does CSS stand for?",
      options: [
        "Computer Style Sheets",
        "Creative Style Sheets",
        "Cascading Style Sheets",
        "Colorful Style Sheets",
      ],
      correctAnswer: 2,
    },
    {
      question: "What does HTTP stand for?",
      options: [
        "Hypertext Technical Protocol",
        "Hypertext Transfer Protocol",
        "High Transfer Text Protocol",
        "Hyper Transfer Text Protocol",
      ],
      correctAnswer: 1,
    },
    {
      question: "Which language is primarily used for web scripting?",
      options: ["JavaScript", "Python", "C++", "Java"],
      correctAnswer: 0,
    },
    {
      question: "What does SQL stand for?",
      options: [
        "Standard Question Language",
        "Simple Query Language",
        "Sequential Query Language",
        "Structured Query Language",
      ],
      correctAnswer: 3,
    },
    {
      question: "What is the main function of a web server?",
      options: [
        "To store data",
        "To run applications",
        "To serve web pages to clients",
        "To protect networks",
      ],
      correctAnswer: 2,
    },
    {
      question: "Which company developed the Java programming language?",
      options: ["Sun Microsystems", "Microsoft", "IBM", "Apple"],
      correctAnswer: 0,
    },
    {
      question: "What is the purpose of the <title> tag in HTML?",
      options: [
        "To create a new section",
        "To define the title of the web page",
        "To add a comment",
        "To include a script",
      ],
      correctAnswer: 1,
    },
    {
      question: "What does API stand for?",
      options: [
        "Application Program Interface",
        "Advanced Programming Interface",
        "Application Programming Interface",
        "Automated Program Interface",
      ],
      correctAnswer: 2,
    },
    {
      question: "What is the purpose of a database index?",
      options: [
        "To store large files",
        "To create backups",
        "To manage user permissions",
        "To speed up data retrieval",
      ],
      correctAnswer: 3,
    },
    {
      question:
        "Which protocol is commonly used for secure communication over the internet?",
      options: ["HTTPS", "FTP", "HTTP", "SMTP"],
      correctAnswer: 0,
    },
  ],

  selectAnswer: (optionIndex) =>
    set((state) => {
      const answers = [...state.answers];
      answers[state.currentQuestion] = optionIndex;
      return { answers };
    }),

  nextQuestion: () =>
    set((state) => {
      const isLastQuestion =
        state.currentQuestion === state.questions.length - 1;

      if (isLastQuestion) {
        let score = 0;

        state.questions.forEach((question, index) => {
          if (state.answers[index] === question.correctAnswer) {
            score++;
          }
        });

        return { showScore: true, score };
      }

      return { currentQuestion: state.currentQuestion + 1 };
    }),

  prevQuestion: () =>
    set((state) => ({
      currentQuestion: Math.max(state.currentQuestion - 1, 0),
    })),

  resetQuiz: () =>
    set(() => ({
      currentQuestion: 0,
      answers: Array(3).fill(null),
      score: 0,
      showScore: false,
    })),
}));

export default useQuizStore;

```

```TSX

//============ App.tsx ============== 

import QuizLayout from "./components/QuizLayout";

function App() {
  return (
    <div className="App">
      <QuizLayout />
    </div>
  );
}

export default App;

```

```TSX

//============ components/QuizLayout.tsx ============== 

import Sidebar from "./Sidebar";
import Question from "./Question";

const QuizLayout = () => {
  return (
    <div className="flex h-screen bg-gray-300">
      <Sidebar />
      <div className="flex-1 flex flex-col items-center justify-center p-6">
        <Question />
      </div>
    </div>
  );
};

export default QuizLayout;

```

```TSX

//============ components/Sidebar.tsx ============== 

import { FaCheckCircle } from "react-icons/fa";
import useQuizStore from "../store/useQuizStore";

const Sidebar = () => {
  const { questions, currentQuestion } = useQuizStore();

  return (
    <div className="w-1/5 pl-5  bg-teal-800 p-4 shadow-md">
      <h2 className="text-xl text-center font-bold mb-4 text-black">Quiz Progress</h2>
      <ul>
        {questions.map((_, index) => (
          <li key={index} className="mb-2 bg-gray-200 rounded-md p-2 flex items-center">
            <FaCheckCircle
              className={`mr-2 ${index <= currentQuestion ? "text-green-600" : "text-gray-800"}`}
            />
            <span className="text-gray-700">Question {index + 1}</span>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default Sidebar;

```

```TSX

//============ components/Question.tsx ============== 

import useQuizStore from "../store/useQuizStore";

const Question = () => {
  const {
    questions,
    currentQuestion,
    selectAnswer,
    answers,
    nextQuestion,
    prevQuestion,
    showScore,
    score,
    resetQuiz,
  } = useQuizStore();

  if (showScore) {
    return (
      <div className="w-3/4 h-3/4 p-6  bg-white shadow-lg rounded-lg flex flex-col items-center justify-center">
        <h2 className="text-2xl font-semibold text-teal-700">Your Score</h2>
        <p className="mt-4 text-lg text-gray-700">
          You scored <span className="font-bold">{score}</span> out of <span className="font-bold">{questions.length}</span>
        </p>
        <button
          onClick={resetQuiz}
          className="mt-6 px-4 py-2 bg-teal-600 text-white rounded hover:bg-teal-700 transition-all"
        >
          Restart Quiz
        </button>
      </div>
    );
  }

  const question = questions[currentQuestion];
  const currentAnswer = answers[currentQuestion];

  const handleSelect = (optionIndex: any) => {
    selectAnswer(optionIndex);
  };

  const handleSubmit = () => {
    nextQuestion();
  };

  return (
    <div className="w-3/4 p-6 border-l-4 border-teal-700 bg-white shadow-lg rounded-lg">
      <h3 className="text-2xl font-semibold text-teal-700"> {question.question}</h3>
      <div className="mt-4">
        {question.options.map((option, index) => (
          <div key={index} className="my-2">
            <label className="flex items-center w-full h-6 border-l-4 rounded-lg p-4 border-teal-700 text-gray-900 cursor-pointer">
              <input
                type="radio"
                name={`question-${currentQuestion}`}
                checked={currentAnswer === index}
                onChange={() => handleSelect(index)}
                className="mr-2 accent-teal-600"
              />

              {option}
            </label>
          </div>
        ))}
      </div>

      <div className="mt-6">
        {currentQuestion > 0 && (
          <button
            onClick={prevQuestion}
            className="mr-4 px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600"
          >
            Previous
          </button>
        )}

        {currentQuestion < questions.length - 1 ? (
          <button
            onClick={nextQuestion}
            className="px-4 py-2 bg-teal-600 text-white rounded hover:bg-teal-700"
          >
            Next
          </button>
        ) : (
          <button
            onClick={handleSubmit}
            className="px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600"
          >
            Submit
          </button>
        )}
      </div>
    </div>
  );
};

export default Question;

```