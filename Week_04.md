## Guidance
Answer the following questions considering the learning outcomes for
- [Week 04](https://learn.foundersandcoders.com/course/syllabus/developer/week04-project03-frontend/learning-outcomes/)


# Weekly Learning Outcomes

- **Collaboration with Mentor**  
  This week, I had the opportunity to work with one of the mentors, Gui, who showed me industry standards for creating TypeScript types and interfaces, particularly using a utils folder.

- **Areas for Improvement**  
  I’m still trying to grasp the concepts of **states**, **props**, and **context** in React. To improve my understanding, I plan to:
  - Revisit the TypeScript documentation.
  - Discuss these topics with my manager.
  - Look into the React documentation, as it is well-documented and helpful for learning.

- **Achievements**  
  - **Creating Interfaces**  
    One of my achievements this week was defining an interface for component props:
    ```typescript
    export interface LabelProps {
        htmlFor: string;
        children: React.ReactNode;
        className: string;
    }
    ```
    Although I received some guidance, I need to delve deeper into understanding `children`, as I see a lot of content related to parent, child, and grandchild props.

  - **Dynamic Rendering with Spotify API**  
    I successfully implemented dynamic rendering of genres using Spotify API JSON data. Initially, I had the genres appearing in uppercase, and not all genres were preloaded in the dropdown. I learned that the Spotify API wouldn't recognize them unless I used `.toLowerCase()`. Here’s the code I wrote for the dropdown:
    ```typescript
    <select
        name='genre'
        id='genre'
        value={selectedGenre}
        onChange={handleGenreChange}
        className='mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md'
    >
        <option value=''>--Please choose an option--</option>
        {genresData.categories.map((genre, index) => (
            <option key={index} value={genre}>
                {genre}
            </option>
        ))}
    </select>
    ```

  - **Component Creation**  
    I created components for each form input. This was relatively simple, as Jason handled the core logic of states and rendered these components when the states changed. However, I still need to look deeper into what is happening in React.
    ![image](https://github.com/user-attachments/assets/aafaf678-0756-40ea-8687-e57355f30d9e)


  - **CSS Skills with Tailwind**  
    Although Tailwind CSS simplifies styling with shorthand classes, I realized I still have a lot to learn about CSS. This is something I will work on in the future. 

- **Understanding TypeScript Config Files**  
  I'm learning how TypeScript configuration files work. Here are some key configurations I’ve been focusing on:
  ```typescript
  {
     "target": "es2016",
     "module": "commonjs",
     "rootDir": "./src",
     "outDir": "./dist",
     "removeComments": true,
     "noEmitOnError": true,
     "strict": true,
     "forceConsistentCasingInFileNames": true,
     "noUnusedLocals": true,
     "noImplicitThis": true
  }
   ```

  - I'll also be doing some node work in the meantime to truly wrap my head around backend. As i like the idea of backend Which just seems so facinating but difficult as of right now. Creating a Neighbour hoood watch. Using get Requests.
  i understand how api works a bit better now. Creating my own Api is something i want to give a go.
    
## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
