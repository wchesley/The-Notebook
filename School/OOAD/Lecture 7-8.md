# Structural Modeling
- Object Identification
- Create CRC cards
- Class diagrams
- object diagrams
- relationship among the structural models. 
- relationship between the structural and functional models. 

## Structural Modeling
- supports the creation of an internal *structural or static view* of a business information system. 
	- it shows hwo the system is structured to support the underlying business processes. 
- **A structural model** is a formal way of representing the objects that are used and created by a business system

## Analysis vs. Design Models
- Analysts: 
	- draw a conceptual model
		- logical organization of the objects
		- free from any implementation or technical details
- Designers:
	- evolve the conceptual structural model into a design model
		- shows how the objects will be organized in databases and software  

## Structural Modeling 
- Represent the things, ideas or concepts contained in the **domain of the problem**  
- representitive of the relationships among the things, ideas or concepts. 
- create the vocabulary necessary for the analyst and users to communicate effectively. 

## Object Identification
- **Textual analysis** Of use case information
	- nouns suggest clauses
	- verbs suggest operations
- **Brainstorming:** People offering ideas
	- start thinking fast and furiously
	- initial list of classes (objects) is developed
	- initial list is then refined
	- attributes, operations and relationships ot other classes can be assigned in a second round. 
- **Common Object Lists** 
	- Physical things(books, desks, chairs, equipment) 
	- Incidents/events (meetings, flights, appointments, etc...)
	- Roles (doctors, patient, nurse, librarian, student)
	- Interactions(sales transaction)
	- Others (place, containers, organizations, business records, catalogs, and policies or even processes)
- **Patters**
	- useful groupings of collaborating classes that provide solutions to common problems (are reuseable)
	- developed patterns provide a starting point for work in similar domains. 
	
---

### Example: 
Assume the library wants to develop a system that tracks library items check outs/ins. the item could be a book, a digital media (CD's films, ebooks, etc) or a device (laptop, ipad, clicker, pointer, etc). The itemshave different checkout strategies, for example a book can be checked out for up to 2 weeks while a laptop for a maximum of 2 days. the patrons are students faculty and staff. each item has a location, and the location could be an open shelf, or a locked safe. the system has to keep track of where the item is at. when the item is checked-in the librarian is responsible for returning it to the proper location an dupdating the inventory. 
1. Draw a use-case diagram for this system
2. What would be candidate objects of this system? 
3. What attributes might these objects have? 
4. List some of their possible behaviors
5. Explain the relationship between these objects (write a diagram)
 
- What attributes these objects may have? 
	- Item (id, location, checkout-strategy, checkedout, quantity, condition,..) 
	- book (title, author, publisher, p-year,..) 
	- digital media (type, publisher, p-year,…) 
	- device (model, type, specs, year,…) 
	- patron (id, name, address, phone#, email,…) 
	- Student (Sid, college, dept, …) 
	- faculty (Fid, college, dept, …) 
	- Staff (Uid, dept, jobTitle, ..) 
	- librarian(Lid, job,  …) 
	- location (building, floor, AccessLevel ) 
	- open shelfs(Section, Shelf#,…) 
	- locked safe( Section, Safe#, keyType, AccessLevel, …) 
	- Inventory (item_Id, Count,…)

- List some of their possible behaviors 
	- Item (addItem(), getLocation(), checkOutItem(), checkInItem(), getStatus()) 
	- book (addBook(), getAuthor(), getPublisher,..) 
	- digital media (addDM(), getType(), getPublisher(),updateStatus(),…) 
	- device (addDevice(),getModel(), getSpecs(),…) 
	- patron (addPatron(),removePatron(),getInfo(),updateInfo(),…) 
	- Student (addStud(),getInfo(), …) 
	- faculty (addFac(),updateFacInfo(), …) 
	- Staff (addStaff(),getStaffCheckedBooks(), ..) 
	- librarian(addLibrarian(),…) 
	- location (addLocation(),updateLocation(),getLocationInf()) 
	- open shelfs( addNewShelf(), updateShelfInfo(),…) 
	- locked safe(updateAccessLevel(), changeKey(), …) 
	- Inventory (update()) 


---

## Class-Responsibility-Collaboration -CRC CARDS
- Used to document the essential properties of a class
- uncover missing properties
- **Responsibilities:**
	- Two seperate types: (Knowing and doing) 
		- Knowing Responsibilities: Things that an instance of a class must be capable of knowing. 
			- Eg; an instance of a class typically knows the values of it's attributes and it's relationships
		- Doing Responsibilities: Things that an instance of a class must be capable of doing 
			- eg; an instance of a class can execute its operations or it can request a second instance, which it knows about, to execute one of it's operations on behalf of the first instance. 
- **Collaborations:**
	- Object (client) request other object(Server) to execute some operation (remote API call?)
	
