## Guidance
Answer the following questions considering the learning outcomes for
- [Week 05](https://learn.foundersandcoders.com/course/syllabus/developer/week05-project03-test-deploy/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
This week i we listed on all the the tasks yet to be completed. To reach our mvp. 
i wanted to get use to doing more react. I had to create a react radio component as it was initally placed in the rendered page with the logic behind the component. 
```typescript
interface RadioProps {
	selectedQuant: number;
	setQuant: (num: number) => void;
}

export default function Radio({ selectedQuant, setQuant }: RadioProps) {
	return (
		<div className='flex justify-center space-x-4'>
			{[5, 10, 15].map((num) => (
				<button
					key={num}
					type='button'
					onClick={() => setQuant(num)}
					className={`w-12 h-12 rounded-full ${
						selectedQuant === num ? 'bg-purple-600' : 'bg-purple-400'
					} text-white flex items-center justify-center focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2`}
				>
					{num}
				</button>
			))}
		</div>
	);
}
```
calling this function in my inputPage utilising state managment. This logic was added when calling for the functional component. 

```typescript
selectedQuant={userResponse.playlistCount}
								setQuant={(num: number) =>
									setUserResponse((prev) => ({ ...prev, playlistCount: num }))
```


 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
this week has been a pain with trying to set up aws credentials. Trying to host my static front-end using an s3 bucket then moving onto an Github pages jekyll. Using all
right commands in my YML file. Yet it was failing when connecting to AWS credentials. 

![image](https://github.com/user-attachments/assets/38f22994-34f3-44a4-afdf-1724db1e8b48)

i prompted chatgpt alot and couldn't figure out why it wasn't conguring the aws credentials. 
Error: Not authorized to perform sts:AssumeRoleWithWebIdentity
searching for this error. 
![image](https://github.com/user-attachments/assets/d19a64e4-a8fb-4c4c-80dc-0b724ac2797d)



## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
