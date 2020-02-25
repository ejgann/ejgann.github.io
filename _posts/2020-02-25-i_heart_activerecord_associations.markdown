---
layout: post
title:      "I [heart] ActiveRecord Associations"
date:       2020-02-25 07:32:17 -0500
permalink:  i_heart_activerecord_associations
---

I haven't always appreciated ActiveRecord Associations. In fact, I used to loathe having to deal with them when I was first starting to learn Rails. But that was due to the fact that I didn't fully understand them. Now, I really like thinking about models' relationships and kind of geek out when I get to draw the models' relationships before creating them in ActiveRecord.

I heard that.... you just groaned. That's fine. My goal is to have you at least slightly intrigued by associations by the end of this article or to at least appreciate how they work within a Rails project. 

Let's say you are working on a Rails project to keep track of medical appointments and, more specifically, which patients have seen which doctors. The doctor and patient models exist independently of one another, but their relationship exists through the appointment model. In other words, a patient sees a doctor by making an appointment and visa versa. That relationship is referred to as a "has_many, through" relationship; the appointment model has a "belongs_to" relationship with both the patient and doctor models:  

* Patients have many doctors through their appointments
* Doctors have many patients through their appointments
* Appointments "belong to" both patients and doctors

While we can write and talk about the models' relationships, Rails does not know their connections to one another. Cue ActiveRecord Associations!

ActiveRecord Associations will map the relationships and create associations in our database so that our project will work as required. There are two main components to creating these associations for Rails. The first is the individual models' files, and the second is Rails migrations that we must write. 

When I open my doctor model file, I see the following:

```
class Doctor < ActiveRecord::Base

     has_many :appointments
		 has_many :patients, through: :appointments

end
```

It is the `ActiveRecord::Base` portion that is responsible for linking the database and the model. The "has_many" portion tells Rails that there are other models in the program and that the doctor model is related to them through a "has_many" relationship. In other words, doctors have many patients through appointments. Similar coding appears in the patient model file:

```
class Patient < ActiveRecord::Base

     has_many :appointments
		 has_many :doctors, through: :appointments

end
```

The doctor and patient models are now connected through the `through: :appointments` part of the code. In other words, Rails will now understand `@patient.doctor` whenever that code appears. But what about the appointments model? How can its role in this relationship be established so it can be recognized in Rails? I'm glad you asked!

```
class Appointment < ActiveRecord::Base

     belongs_to :doctor
		 belongs_to :patient

end
```

The model files now reflect the models' relationships, but now we need to ensure that our database also recognizes the relationships. The next step is to write a database migration so that the models' individual tables can be associated with one another. *Note:  I am going to spend more time with migrations in a later blog post. But, for now, know that it is one of the two essential pieces to successfully establishing associations in Rails. Stay tuned!*

### Conclusion

So there you have it. Rails, through ActiveRecord, is now able to access and store the interconnected data between the doctor and patient models through the appointments model. So, now, if you needed to know which doctors a specific patient has seen, you can find that information by accessing that patient's appointments. Or, let's say that you want to get a list of all patients that a specific doctor has seen. You would access that doctor's appointments to retrieve her list of patients. While you may not love this topic as much as I do, I hope that I have helped to explain a sometimes-complex topic in a friendlier way.


