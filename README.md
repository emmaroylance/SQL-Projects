# The-Tech-Academy-Basic-SQL-Projects
This repository showscases my SQL project that creates a library database with 7 tables and executes 7 procedures. 


Here is the code I created to do so:

	CREATE DATABASE db_library;
	USE db_library;

	/*Create Tables */

	CREATE TABLE Library_Branch (
		BranchID int PRIMARY KEY NOT NULL IDENTITY (100, 1),
		BranchName VARCHAR(50) NOT NULL,
		Address VARCHAR(50) NOT NULL
	);

	SELECT * FROM Library_Branch;

	CREATE TABLE Publisher (
		PublisherName VARCHAR(50) PRIMARY KEY NOT NULL,
		Address VARCHAR(50) NOT NULL,
		Phone VARCHAR(50) NOT NULL
	);

	SELECT * FROM Publisher;

	CREATE TABLE Borrower (
		CardNo INT PRIMARY KEY NOT NULL IDENTITY (1, 1),
		Name VARCHAR(50) NOT NULL,
		Address VARCHAR(50) NOT NULL,
		Phone VARCHAR(50) NOT NULL
	);

	SELECT * FROM Borrower;

	CREATE TABLE Books (
		BookID INT PRIMARY KEY NOT NULL IDENTITY (10, 10),
		Title VARCHAR(50) NOT NULL,
		PublisherName VARCHAR(50) NOT NULL CONSTRAINT fk_PublisherName FOREIGN KEY REFERENCES Publisher(PublisherName) ON UPDATE CASCADE ON DELETE CASCADE,
	);

	SELECT * FROM Books 

	CREATE TABLE Book_Authors (
		BookID INT NOT NULL CONSTRAINT fk_BookID FOREIGN KEY REFERENCES Books(BookID) ON UPDATE CASCADE ON DELETE CASCADE,
		AuthorName VARCHAR(50) NOT NULL
	);

	SELECT * FROM BooK_AUTHORS;

	CREATE TABLE Book_Copies (
		BookID INT NOT NULL CONSTRAINT fk_BookIDCopies FOREIGN KEY REFERENCES Books(BookID) ON UPDATE CASCADE ON DELETE CASCADE,
		BranchID INT NOT NULL CONSTRAINT fk_BranchID FOREIGN KEY REFERENCES Library_Branch(BranchID) ON UPDATE CASCADE ON DELETE CASCADE,
		Number_of_Copies INT NOT NULL
	);

	SELECT * FROM BooK_Copies;

	CREATE TABLE Book_Loans (
		BookID INT NOT NULL CONSTRAINT fk_BookIDLoans FOREIGN KEY REFERENCES Books(BookID) ON UPDATE CASCADE ON DELETE CASCADE,
		BranchID INT NOT NULL CONSTRAINT fk_BranchIDLoans FOREIGN KEY REFERENCES Library_Branch(BranchID) ON UPDATE CASCADE ON DELETE CASCADE,
		CardNo INT NOT NULL CONSTRAINT fk_CardNo FOREIGN KEY REFERENCES Borrower(CardNo) ON UPDATE CASCADE ON DELETE CASCADE,
		DateOut Date NOT NULL,
		DateIn Date NOT NULL
	);

	SELECT * FROM Book_loans;

	/*Insert Values into Tables */

	INSERT INTO Library_Branch
		(BranchName, Address)
		VALUES
		('Sharpstown','810 E 3300 S, Millcreek, UT 84106'),
		('Central','8041 Wood St, Midvale, UT 84047'),
		('Murray','166 E 5300 S, Murray, UT 84107'),
		('Provo','550 N University Ave, Provo, UT 84601')
	;
	SELECT * FROM Library_Branch;

	INSERT INTO Publisher
		(PublisherName, Address, Phone)
		VALUES
		('Family Heritage Publishers','1154 Bateman Point Dr, West Jordan, UT 84084','(801) 685-9188'),
		('Next Century Publishing','10701 S River Front Pkwy, South Jordan, UT 84095','(801) 441-2071'),
		('WiDo Publishing','840 S W Temple #2, Salt Lake City, UT 84101','(585) 326-4599')
	;

	SELECT * FROM Publisher;

	INSERT INTO Borrower
		(Name, Address, Phone)
		VALUES
		('John Doe', '789 Main Street', '(123) 456-7890'),
		('Mary Smith', '435 Shadow Wood Drive', '(234) 567-8901'),
		('Bob Maines', '899 Crop Tree Circle', '(345) 678-9012'),
		('Jordan Ewell', '1212 Rosemary Lane', '(456) 789-0123'),
		('Ben Gilmore', '4010 Bushel Road', '(567) 890-1234'),
		('Aja Collins', '302 Water Springs Drive', '(678) 901-2345'),
		('Brad Thompson', '874 Walden Meadows Drive', '(789) 012-3456'),
		('Mazy Jorgensen', '989 Vine St', '(890) 123-4567')
	;
	SELECT * FROM Borrower;

	INSERT INTO Books
		(Title, PublisherName)
		VALUES
		('The Ligtning Thief', 'Family Heritage Publishers'),
		('Twilight', 'Next Century Publishing'),
		('The Hunger Games', 'WiDo Publishing'),
		('The Giver', 'Next Century Publishing'),
		('Number the Stars', 'Next Century Publishing'),
		('Gathering Blue', 'Next Century Publishing'),
		('City of Bones', 'Family Heritage Publishers'),
		('The Fault in Our Stars', 'Next Century Publishing'),
		('Looking for Alaska', 'Next Century Publishing'),
		('Divergent', 'WiDo Publishing'),
		('Insurgent', 'WiDo Publishing'),
		('Allegiant', 'WiDo Publishing'),
		('Four', 'WiDo Publishing'),
		('To Kill a Mockingbird', 'WiDo Publishing'),
		('A Summer to Die', 'Next Century Publishing'),
		('The Book Thief', 'Family Heritage Publishers'),
		('The Hobbit', 'Family Heritage Publishers'),
		('The Shining', 'WiDo Publishing'),
		('It', 'WiDo Publishing'),
		('A Wrinkle in Time', 'Family Heritage Publishers')
	;

	SELECT * FROM Books;
	SELECT * FROM Library_Branch;

	INSERT INTO Book_Authors
		(BookID, AuthorName)
		VALUES
		(10, 'Rick Riordan'),
		(20, 'Stephenie Meyer'),
		(30, 'Suzanne Collins'),
		(40, 'Lois Lowry'),
		(50, 'Lois Lowry'),
		(60, 'Lois Lowry'),
		(70, 'Cassandra Clare'),
		(80, 'John Green'),
		(90, 'John Green'),
		(100, 'Veronica Roth'),
		(110, 'Veronica Roth'),
		(120, 'Veronica Roth'),
		(130, 'Veronica Roth'),
		(140, 'Harper Lee'),
		(150, 'Lois Lowry'),
		(160, 'Markus Zusak'),
		(170, 'J.R.R. Tolkien'),
		(180, 'Stephen King'),
		(190, 'Stepen King'),
		(200, 'Madeleine L''Engle')
	;

	SELECT * FROM Book_Authors;

	INSERT INTO Book_Copies
		(BookID, BranchID, Number_of_Copies)
		VALUES
		(10,100,2),
		(10,101,2),
		(10,102,2),
		(10,103,2),
		(20,100,2),
		(20,101,2),
		(20,102,2),
		(20,103,2),
		(30,100,2),
		(30,101,2),
		(30,102,2),
		(30,103,2),
		(40,100,2),
		(40,101,2),
		(40,102,2),
		(40,103,2),
		(50,100,2),
		(50,101,2),
		(50,102,2),
		(50,103,2),
		(60,100,2),
		(60,101,2),
		(60,102,2),
		(60,103,2),
		(70,100,2),
		(70,101,2),
		(70,102,2),
		(70,103,2),
		(80,100,2),
		(80,101,2),
		(80,102,2),
		(80,103,2),
		(90,100,2),
		(90,101,2),
		(90,102,2),
		(90,103,2),
		(100,100,2),
		(100,101,2),
		(100,102,2),
		(100,103,2),
		(110,100,2),
		(110,101,2),
		(110,102,2),
		(110,103,2),
		(120,100,2),
		(120,101,2),
		(120,102,2),
		(120,103,2),
		(130,100,2),
		(130,101,2),
		(130,102,2),
		(130,103,2),
		(140,100,2),
		(140,101,2),
		(140,102,2),
		(140,103,2),
		(150,100,2),
		(150,101,2),
		(150,102,2),
		(150,103,2),
		(160,100,2),
		(160,101,2),
		(160,102,2),
		(160,103,2),
		(170,100,2),
		(170,101,2),
		(170,102,2),
		(170,103,2),
		(180,100,2),
		(180,101,2),
		(180,102,2),
		(180,103,2),
		(190,100,2),
		(190,101,2),
		(190,102,2),
		(190,103,2),
		(200,100,2),
		(200,101,2),
		(200,102,2),
		(200,103,2)
	;

	SELECT * FROM Book_Copies;
	SELECT * FROM Borrower;
	SELECT * FROM Library_Branch;
	SELECT * FROM Books;

	UPDATE Books SET Title = 'The Lost Tribe' WHERE Title = 'The Hobbit';
	UPDATE Book_Authors SET AuthorName = 'Edward Marriott' WHERE AuthorName = 'J.R.R. Tolkien';

	INSERT INTO Book_Loans
		(BookID, BranchID, CardNo, DateOut, DateIn)
		VALUES
		(10,100,1,'20190601','20191202'),
		(20,100,1,'20190601','20191202'),
		(30,100,1,'20190601','20191202'),
		(40,100,1,'20190601','20191202'),
		(50,100,1,'20190601','20191202'),
		(60,100,1,'20190601','20191202'),
		(70,100,1,'20190601','20191202'),
		(90,100,1,'20190601','20191202'),
		(160,101,2,'20190602','20190615'),
		(170,101,2,'20190602','20190615'),
		(180,101,2,'20190602','20190615'),
		(190,101,2,'20190602','20190615'),
		(200,101,2,'20190602','20190615'),
		(10,101,2,'20190602','20190615'),
		(20,101,2,'20190602','20190615'),
		(30,101,2,'20190602','20190615'),
		(40,101,2,'20190602','20190615'),
		(50,102,3,'20190603','20190616'),
		(60,102,3,'20190603','20190616'),
		(70,102,3,'20190603','20190616'),
		(80,102,3,'20190603','20190616'),
		(90,102,3,'20190603','20190616'),
		(100,102,3,'20190603','20190616'),
		(110,102,4,'20190604','20190617'),
		(120,102,4,'20190604','20190617'),
		(130,102,4,'20190604','20190617'),
		(140,102,4,'20190604','20190617'),
		(150,102,4,'20190604','20190617'),
		(160,102,4,'20190604','20190617'),
		(10,103,5,'20190605','20190618'),
		(20,103,5,'20190605','20190618'),
		(50,103,5,'20190605','20190618'),
		(60,103,5,'20190605','20190618'),
		(80,103,5,'20190605','20190618'),
		(90,103,5,'20190605','20190618'),
		(10,103,6,'20190606','20190619'),
		(20,103,6,'20190606','20190619'),
		(30,103,6,'20190606','20190619'),
		(200,103,6,'20190606','20190619'),
		(180,103,6,'20190606','20190619'),
		(150,103,6,'20190606','20190619'),
		(100,100,7,'20190607','20190620'),
		(110,100,7,'20190607','20190620'),
		(120,100,7,'20190607','20190620'),
		(130,100,7,'20190607','20190620'),
		(140,100,7,'20190607','20190620'),
		(150,100,7,'20190607','20190620'),
		(50,101,8,'20190608','20190621'),
		(60,101,8,'20190608','20190621'),
		(70,101,8,'20190608','20190621'),
		(80,101,8,'20190608','20190621'),
		(90,101,8,'20190608','20190621'),
		(100,101,8,'20190608','20190621')
	;
	SELECT * FROM Book_Loans;
	GO
	/* Procedures */

	/*#1 */

	SELECT * FROM Library_Branch;
	SELECT * FROM Books;
	SELECT * FROM Book_Copies;
	go

	CREATE PROC #1
	AS
	SELECT 
	Library_Branch.BranchName, Book_Copies.Number_of_Copies, Books.Title
	FROM Book_Copies
	INNER JOIN Library_Branch ON Library_Branch.BranchID = book_copies.BranchID 
	INNER JOIN Books ON Books.BookID = Book_Copies.BookID
	WHERE Books.BookID = 170 AND Library_Branch.BranchID = 100
	;
	GO
	EXEC #1


	/* #2 */
	CREATE PROC #2
	AS
	SELECT 
	Library_Branch.BranchName, Book_Copies.Number_of_Copies, Books.Title
	FROM  Book_Copies
	INNER JOIN Library_Branch ON library_branch.BranchID = Book_Copies.BranchID
	INNER JOIN Books ON Books.BookID = Book_Copies.BookID
	WHERE Books.BookID = 170
	;
	EXEC #2;
	GO

	/* #3 */
	SELECT * FROM Borrower;
	SELECT * FROM Book_Loans;
	GO
	CREATE PROC #3
	AS
	SELECT 
		Borrower.Name
		FROM Book_Loans
		INNER JOIN Borrower ON Borrower.CardNo = Book_Loans.CardNo
	WHERE NOT EXISTS(SELECT Book_loans.cardno FROM Book_loans WHERE	Borrower.CardNo = Book_Loans.CardNo)
	;
	EXEC #3

	/* #4 */

	SELECT * FROM Library_Branch;
	SELECT * FROM Book_Loans;
	SELECT * FROM Borrower;
	SELECT * FROM Books;
	GO

	CREATE PROC #4
	AS
	SELECT
		Books.Title, Borrower.Name, Borrower.Address
	FROM Book_Loans
	INNER JOIN Books ON Books.BookID = Book_Loans.BookID
	INNER JOIN Borrower ON Borrower.CardNo = Book_Loans.CardNo
	INNER JOIN Library_Branch ON Library_Branch.BranchID = Book_Loans.BranchID
	WHERE DateIn >=DATEADD(day, DATEDIFF(day,0,GETDATE()),0) 
	AND DateIn < DATEADD(day, DATEDIFF(day,0,GETDATE())+1,0)
	;
	EXEC #4

	/* #5 */
	SELECT * FROM Book_Copies;
	SELECT * FROM Library_Branch;
	SELECT * FROM Book_Loans;
	GO

	CREATE PROC #5
	AS
	SELECT
		COUNT(*) BookID, Library_Branch.BranchName
		FROM Book_Loans		
		INNER JOIN Library_Branch ON Library_Branch.BranchID = Book_Loans.BranchID
		INNER JOIN Book_Copies ON Book_Copies.BookID = Book_Loans.BookID
		GROUP BY Library_Branch.BranchName
	;
	EXEC #5

	/* #6 */

	SELECT * FROM Borrower;
	SELECT * FROM Book_Loans;
	GO
	CREATE PROC #6
	AS
	SELECT 
		COUNT(Book_Loans.CardNo ), Borrower.Name, Borrower.Address
	FROM Book_Loans
	INNER JOIN Borrower ON Borrower.CardNo = Book_Loans.CardNo
	GROUP BY Borrower.Name, Borrower.Address
	HAVING COUNT(Book_Loans.CardNo ) > 5  
	;
EXEC #6


	/* #7 */

	SELECT * FROM Book_Authors;
	SELECT * FROM Books;
	SELECT * FROM Library_Branch;
	SELECT * FROM Book_Copies;

	GO

	CREATE PROC #7
	AS
	SELECT
		Books.Title, Book_Copies.Number_of_Copies
		FROM Book_Copies
		INNER JOIN Books ON Books.BookID = Book_Copies.BookID
		INNER JOIN Library_Branch ON Library_Branch.BranchID = Book_Copies.BranchID
		INNER JOIN Book_Authors ON Book_Authors.BookID = Book_Copies.BookID
		WHERE Book_Authors.AuthorName = 'Stephen King' AND Library_Branch.BranchName = 'Central'
	;

	EXEC #7;
