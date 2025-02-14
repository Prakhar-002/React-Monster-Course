
<h1  align="center" > 🍄 𝐏𝗋ⱺρ𝗌 𝐂ɦ𝗂ᥣᑯ𝗋𝖾𐓣 🥠</h1>

``` JSX

import Card from "./components/Card";

const App = () => {
  return (
    <div>
      <h1>My Cards</h1>
      <Card>
        <h2>Card Title 1</h2>
        <p>This is some content for card 1.</p>
      </Card>
      <Card>
        <h2>Card Title 2</h2>
        <p>This is some content for card 2.</p>
      </Card>
      <Card>
        <h2>Card Title 3</h2>
        <p>This is some content for card 3.</p>
      </Card>
    </div>
  );
};

export default App;

```

```JSX

const Card = ({ children }) => {
  return <div>{children}</div>;
};

export default Card;

```
