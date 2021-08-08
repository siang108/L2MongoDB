# L2MongoDB

Exercise
1) Insert documents to a collection called places with the following criteria:
a) THREE (3) places (name field) in any country including Italy (country field) that 
have different number of likes, eg: some places will have more likes and some will 
have less like.
db.places.insert({name:"Bandar Hilir",country:"Malaysia",description:"Historical City",tags:["historical","Hang Tuah"], likes:100})
db.places.insert({name:"Paris",country:"France",description:"City of love",tags:["love","shopping","historical"], likes:25})
db.places.insert({name:"Venice",country:"Italy",description:"City of canals",tags:["cruise","boating","historical"], likes:50})

b) THREE (3) places (name field) each in France and Malaysia (country) that have 
new items which are comments (array of object (user)) that has user name, message 
and rating (0-100) as items.
comments:[{user1},{user2},{user3}]
db.places.insert({name:"Brittany",country:"France",description:"Historic Ports",tags:["fishing","ports","beaches"], likes:80, comments:[{user:"user1", message: "My first comment", rating:"90" }, {user:"user2", message: "My second comment", rating: "80"}]})
db.places.insert({name:"Eiffel Tower",country:"France",description:"Symbol of Paris",tags:["restaurant","tower","landmarks"], likes:62, comments:[{user:"user1", message: "My first comment", rating:"92" }, {user:"user2", message: "My second comment", rating: "82"},{user:"user3", message: "My third comment", rating: "72"}]})
db.places.insert({name:"Mont Saint-Michel",country:"France",description:"The Pyramid of the Seas",tags:["church","coast","defensive walls"], likes:63, comments:[{user:"user1", message: "My first comment", rating:"93" }, {user:"user2", message: "My second comment", rating: "83"},{user:"user3", message: "My third comment", rating: "73"}]})
db.places.insert({name:"Cameron Highlands",country:"Malaysia",description:"Emerald green hill ",tags:["tea estates","lavender farms","rafflesia"], likes:134, comments:[{user:"user1", message: "My first comment", rating:"131" }, {user:"user2", message: "My second comment", rating: "141"},{user:"user3", message: "My third comment", rating: "151"}]})
db.places.insert({name:"Sipadan Island",country:"Malaysia",description:"The ocean",tags:["diving","marine habitat","whale sharks","turtle","corals"], likes:155, comments:[{user:"user1", message: "My first comment", rating:"132" }, {user:"user2", message: "My second comment", rating: "142"},{user:"user3", message: "My third comment", rating: "152"}]})
db.places.insert({name:"Mount Kinabalu",country:"Malaysia",description:"The tallest mountain in Malaysia",tags:["grassland","climbers","National Park","4000 meters high"], likes:123, comments:[{user:"user1", message: "My first comment", rating:"133" }, {user:"user2", message: "My second comment", rating: "143"},{user:"user3", message: "My third comment", rating: "153"}]})

2) Retrieve all the places.
db.places.find()
db.places.find().pretty()

3) Retrieve all the places in France.
db.places.find({country:"France"}).pretty()

4) Get the query to get the top 3 highest likes places in your database.
db.places.find().sort({likes:-1}).limit(3).pretty()
db.places.find({},{name:1}).sort({likes:-1}).limit(3).pretty()
db.places.find({},{name:1,_id:0}).sort({likes:-1}).limit(3).pretty()

5) Get the query of top 3 highest likes places in Malaysia.
db.places.find({"country":"Malaysia"}).sort({likes:-1}).limit(3).pretty()

6) Get the query to get a place in France that has likes more than 80.
db.places.find({"country":"France","likes":{$gt:80}}) 
7) Return all the places in France and Italy.
db.places.find({"country": {$in: ["France", "Italy"]}})
