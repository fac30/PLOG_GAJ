## Guidance
Answer the following questions considering the learning outcomes for
- [Week 06](https://learn.foundersandcoders.com/course/syllabus/developer/week06-project04-databases/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
-This week was challenging as I was ill, but I continued working from home using SelectStarSQL.com to strengthen my understanding of SQL basics. I focused on learning about relationships like one-to-many, many-to-one, and one-to-one, and how to think more broadly when designing a database, especially when things evolve into microservices.

-This week was challenging as I was ill, but I continued working from home using SelectStarSQL.com to strengthen my understanding of SQL basics. I focused on learning about relationships like one-to-many, many-to-one, and one-to-one, and how to think more broadly when designing a database, especially in the context of building systems that could eventually evolve into microservices. This approach ensures that the database is modular and can scale as different components of the application are split into individual services.
```typescript
export const getArtistById = (req: Request, res: Response) => {
	//get endpoints for artist with particular id:
	const { id } = req.params;
	const stmt = db.prepare('SELECT name FROM artists WHERE id = ?');
	const artist = stmt.get(id);
	if (artist) {
		res.json(artist);
	} else {
		res.status(404).json({ message: 'Artist not found' });
	}
};


```
-i'll like to work with dani on front end so i have a better understanding on hooks in react. As some teams show cased react router context. 

## Feedback (For CF's)
> [**Course Facilitator name**]
Alexander
It is great that you are getting some knowdlege on SQL, you mentioned that you like BE, so SQL it's a must for you. You could add some code snippets and explain some basic concepts like what is a Foreign Key, how are the relationships actually built, etc
