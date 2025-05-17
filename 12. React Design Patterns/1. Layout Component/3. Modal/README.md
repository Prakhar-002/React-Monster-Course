
<h1  align="center" > 🍄 𝐌ⱺᑯαᥣ 🥠</h1>

``` JSX
//============ ⚛️App.tsx ============== 

import GamesInfo from "./components/GamesInfo";
import Modal from "./components/Modal";
import { games } from "./data/data";

const App = () => {
  return (
    <>
      <Modal>
        <GamesInfo data={games} />
      </Modal>
    </>
  );
};

export default App;

```

</br>

``` JSX
//============ 🗂️components/⚛️Model.tsx ============== 

import { useState, ReactNode } from "react";

const Modal = ({ children }: { children: ReactNode }) => {
  const [shouldShow, setShouldShow] = useState(false);

  return (
    <>
      <button
        className="border p-5 bg-gray-300"
        onClick={() => setShouldShow(true)}
      >
        Show Modal
      </button>

      {shouldShow && (
        <section
          className="fixed left-0 top-0 z-index-10 w-screen h-full overflow-auto bg-black bg-opacity-50"
          onClick={() => setShouldShow(false)}
        >
          <div
            className="bg-white mx-[10%] my-auto p-[20px] w-[50%]"
            onClick={(e: React.MouseEvent<HTMLDivElement>) =>
              e.stopPropagation()
            }
          >
            <button
              className="border p-5 bg-gray-300"
              onClick={() => setShouldShow(false)}
            >
              Hide Modal
            </button>
            {children}
          </div>
        </section>
      )}
    </>
  );
};

export default Modal;

```

</br>

``` JSX
//============ 🗂️components/⚛️GamesInfo.tsx ============== 

interface Game {
  gameName: string;
  gameRating: number;
  gameGenre: string;
  gameLanguages: string[];
}

interface GamesInfoProps {
  data: Game[];
}

const GamesInfo = ({ data }: GamesInfoProps) => {
  return (
    <div>
      {data.map((d, index) => {
        const { gameName, gameRating, gameGenre, gameLanguages } = d;
        return (
          <div key={index}>
            <h1>Game Name: {gameName}</h1>
            <p>Game Rating: {gameRating}</p>
            <p>Game Genre: {gameGenre}</p>
            <ul>
              Languages:
              {gameLanguages?.map((l, i) => (
                <li key={i}>{l}</li>
              ))}
            </ul>
          </div>
        );
      })}
    </div>
  );
};

export default GamesInfo;

```
