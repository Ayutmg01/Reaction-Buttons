# Reaction-Buttons
A customizable React component for adding interactive reaction buttons to your posts. This component includes various emoji reactions such as like, love, wow, and angry, and provides an intuitive interface for users to express their reactions.
Certainly! Here’s a detailed `README.md` file for your React Reactions component repository:

---

# Reaction-Buttons

A customizable React component for adding interactive reaction buttons to your posts. This component includes various emoji reactions such as like, love, wow, and angry, and provides an intuitive interface for users to express their reactions.

## Features

- **Interactive Emojis**: Includes like, love, wow, and angry reactions.
- **Dynamic Updates**: Reactions update in real-time based on user interaction.
- **Customizable**: Easily modify or extend the reaction types and styles.
- **Responsive Design**: Works well on both desktop and mobile devices.

## Installation

To include the React Reactions component in your project, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/react-reactions.git
   ```

2. **Navigate to the project directory:**
   ```bash
   cd react-reactions
   ```

3. **Install dependencies:**
   ```bash
   npm install
   ```

4. **Run the application:**
   ```bash
   npm run dev
   ```

5. **Open your browser and navigate to:**
   ```bash
   http://localhost:3000
   ```

## Usage

To use the `Reaction` component in your React project, follow these steps:

1. **Import the `Reaction` component:**
   ```javascript
   import Reaction from './path/to/Reaction';
   ```

2. **Include the component in your JSX:**
   ```javascript
   function App() {
     return (
       <div className="App">
         <Reaction />
       </div>
     );
   }

   export default App;
   ```

## Example Code

Here’s an example of how you can use the `Reaction` component in your application:

```javascript
'use client'
import React, { useState } from 'react'
import { BsFillEmojiAngryFill } from "react-icons/bs";
import { ImHappy2 } from "react-icons/im";
import { SlLike } from "react-icons/sl";
import { FcLike } from "react-icons/fc";
import { Button } from '@nextui-org/button';

const Reaction = () => {
  const [postReactions, setPostReactions] = useState({
    angry: 5,
    wow: 1,
    like: 20,
    love: 3
  });

  const [isReactionDivOpen, setIsReactionDivOpen] = useState(false);
  const [reactionType, setReactionType] = useState(null);

  const handleReactionChange = (newReaction) => {
    const reactionsBckUp = { ...postReactions };
    if (newReaction === reactionType) {
      reactionsBckUp[newReaction]--;
      setReactionType(null);
    } else {
      reactionsBckUp[newReaction]++;
      setReactionType(newReaction);
    }
    setPostReactions(reactionsBckUp);
  };

  const generateSelectedReaction = () => {
    if (reactionType === 'angry') {
      return <BsFillEmojiAngryFill onClick={() => handleReactionChange('angry')} size={80} color='crimson' />;
    } else if (reactionType === 'wow') {
      return <ImHappy2 size={80} onClick={() => handleReactionChange('wow')} color="#FFDD8B" />;
    } else if (reactionType === 'love') {
      return <FcLike onClick={() => handleReactionChange('love')} size={80} color="#FFDD8B" />;
    } else {
      return <SlLike onClick={() => handleReactionChange('like')} size={80} color={reactionType && "#89CFF0"} />;
    }
  };

  return (
    <div>
      {isReactionDivOpen && (
        <div className='flex gap-4 p-2 mt-4 ml-4 shadow-lg border justify-center items-center bg-white border-gray-400 w-[30%] rounded-lg'>
          <SlLike size={reactionType === 'like' ? 140 : 80} onClick={() => handleReactionChange('like')} color="#89CFF0" />
          <BsFillEmojiAngryFill size={reactionType === 'angry' ? 140 : 80} onClick={() => handleReactionChange('angry')} color='crimson' />
          <ImHappy2 size={reactionType === 'wow' ? 140 : 80} onClick={() => handleReactionChange('wow')} color="#FFDD8B" />
          <FcLike size={reactionType === 'love' ? 140 : 80} onClick={() => handleReactionChange('love')} color="crimson" />
        </div>
      )}
      <div className='m-2 shadow-lg w-20' onMouseEnter={() => setIsReactionDivOpen(true)}>
        {generateSelectedReaction()}
      </div>
      <div className='flex gap-6 shadow-lg m-4'>
        <div>angry: {postReactions.angry}</div>
        <div>wow: {postReactions.wow}</div>
        <div>like: {postReactions.like}</div>
        <div>love: {postReactions.love}</div>
      </div>
    </div>
  );
}

export default Reaction;
```

## Contributing

Contributions are welcome! If you'd like to contribute, please fork the repository and create a pull request with your changes. Ensure your code follows the project's style guidelines and includes appropriate tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or suggestions, please contact ayutmg456@gmail.com or open an issue in the repository.

---
