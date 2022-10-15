# DatabaseProject
Part 1 of database management
To get this running you will need to make a database in your MYSQL Workbench named "projectdb" in the same way we had to make "testdb" for the exercises. I continued to use the user john and password pass1234 we have been using. Once you make the database you can type all this in and execute it:

use projectdb;
drop table if exists User; 
CREATE TABLE if not exists User( 
    email VARCHAR(50) NOT NULL UNIQUE, 
    firstName VARCHAR(10) NOT NULL, 
    lastName VARCHAR(10) NOT NULL, 
    password VARCHAR(20) NOT NULL, 
    birthday DATE NOT NULL, 
    adress_street_num VARCHAR(5) , 
    adress_street VARCHAR(30) , 
    adress_city VARCHAR(20), 
    adress_state VARCHAR(2),
    adress_zip_code VARCHAR(5),
    eth_bal DECIMAL(13,2) DEFAULT 100,
    PRIMARY KEY (email) ); 
    insert into User(email, firstName, lastName, password, birthday, adress_street_num, adress_street, adress_city, adress_state, adress_zip_code, eth_bal)
    values ('susie@gmail.com', 'Susie ', 'Guzman', 'susie1234', '2000-06-27', '1234', 'whatever street', 'detroit', 'MI', '48202','100'),
            ('sophie@gmail.com', 'Sophie', 'Pierce','sophie1234', '1999-06-15', '2468', 'yolos street', 'ides', 'CM', '24680','100'),
            ('angelo@gmail.com', 'Angelo', 'Francis','angelo1234', '2021-06-14', '4680', 'egypt street', 'lolas', 'DT', '13579','100'),
            ('rudy@gmail.com', 'Rudy', 'Smith','rudy1234', '1996-06-05', '1234', 'sign street', 'samo ne tu','MH', '09876','100'),
            ('jeannette@gmail.com', 'Jeannette', 'Stone','jeannette1234', '2001-04-24', '0981', 'snoop street', 'kojik', 'HW', '87654','100'),
            ('root', 'default', 'default','pass1234', '0000-00-00', '0000', 'Default', 'Default', '0', '00000','100'),
            ('cody@gmail.com', 'Cody', 'Shea','pass1234', '2001-02-24', '28050', 'test street', 'holland', 'MI', '47023','100'),
            ('todd@gmail.com', 'Todd', 'Stone','todd1234', '1993-07-28', '1856', 'fake road', 'detroit', 'MI', '48202','100'),
            ('steven@gmail.com', 'Steven', 'Smith','steven1234', '1998-06-07', '8321', 'madeup street', 'town', 'CO', '14258','100'),
            ('ashley@gmail.com', 'Ashley', 'Thompson','ashley1234', '2002-01-14', '8864', 'garfield street', 'roseville', 'MI', '48066','100');
drop table if exists Nft; 
CREATE TABLE if not exists Nft( 
    nftid int auto_increment NOT NULL UNIQUE, 
    nftname VARCHAR(30) NOT NULL UNIQUE, 
    nftdescription VARCHAR(70) NOT NULL, 
    imagePath VARCHAR(250) NOT NULL,
    userEmail VARCHAR(50) NOT NULL,
	PRIMARY KEY (nftid) ); 
	insert into Nft(nftname, nftdescription, imagePath, userEmail)
    values ('dog', 'dog with an eyepatch', 'https://preview.redd.it/l4jzph3tc5z71.jpg?auto=webp&s=a89013de52f194e2bb2cdf95284cde222654c965', 'jeannette@gmail.com'),
		('eye', 'eyeball and stairs', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSouf5VBg6B0dsD_pzuhX3j4U42EozNN-eyhA&usqp=CAU', 'ashley@gmail.com'),
		('person', 'person drawn in paint', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSB7hRaz5q1seXRoxW-AN4Ptr0d-Ikdc9lquQ&usqp=CAU', 'jeannette@gmail.com'),
		('horses', 'multiple horse NFTs', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRrlBxUzPoJBBNgT15vC_z9iW3HirotMOgesQ&usqp=CAU', 'cody@gmail.com'),
		('pelicans', 'multiple pelican NFTs', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQouK6aSiMxxJa6IaDFFeSMAhYkyw7lzidphA&usqp=CAU', 'rudy@gmail.com'),
		('coin', 'crypto on a skyscraper', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSmGr0jVq6xiRcHgIXt8ACv1r7Ojx1VSVJNrQ&usqp=CAU', 'angelo@gmail.com'),
		('robot', 'robot standing', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQCE3l1dw0l3bYj_s6hKn-J2kvgCc9Mpto5yA&usqp=CAU', 'sophie@gmail.com'),
		('cat', 'fashionable cat', 'https://moon.ly/blog/content/images/2022/03/252.png', 'cody@gmail.com'),
		('clothed coin', 'coin with a hoodie', 'https://metav.rs/assets/uploads/2022/08/fake-NFTs.webp', 'steven@gmail.com'),
		('psychedelic cat', 'smoking cat with psychedelic background', 'https://miro.medium.com/max/1024/0*DFBQ7dyFQWRaOMkV.png', 'susie@gmail.com');
        
drop table if exists Listings; 
CREATE TABLE if not exists Listings( 
    listingsid int auto_increment NOT NULL UNIQUE, 
    nftid int NOT NULL UNIQUE, 
    durationMonths int NOT NULL, 
	dateListed DATE NOT NULL, 
    cost DECIMAL(13,2) NOT NULL,
    activity ENUM('active', 'sold', 'expired') NOT NULL,
	PRIMARY KEY (listingsid) ); 
	insert into Listings(nftid, durationMonths, dateListed, cost, activity)
    values ('3', '2', '2022-09-27', '50', 'sold'),
		('2', '1', '2022-09-20', '100', 'active'),
		('1', '3', '2022-08-20', '75', 'active'),
        ('5', '1', '2022-08-28', '150', 'expired'),
        ('6', '1', '2022-10-05', '2000', 'active'),
        ('7', '2', '2022-07-15', '20', 'expired'),
        ('9', '3', '2022-10-05', '5', 'active'),
        ('10', '1', '2022-10-10', '100', 'sold'),
        ('4', '2', '2022-09-18', '80', 'active'),
        ('8', '2', '2022-09-15', '90', 'sold');
        
drop table if exists Transactions; 
CREATE TABLE if not exists Transactions( 
    transactionid int auto_increment NOT NULL UNIQUE, 
    userEmailBuyer VARCHAR(50) NOT NULL,
    userEmailSeller VARCHAR(50) NOT NULL,
	dateCompleted DATE NOT NULL, 
    transactionType ENUM('transfer', 'sale') NOT NULL,
    nftid int NOT NULL,
	listingsid int,
	PRIMARY KEY (transactionid) ); 
    insert into Transactions(userEmailBuyer, userEmailSeller, dateCompleted, transactionType, nftid, listingsid)
    values ('susie@gmail.com' , 'angelo@gmail.com', '2022-09-19', 'transfer' ,'6', null),
		('susie@gmail.com' , 'jeannette@gmail.com', '2022-09-19', 'sale','3', '1'),
        ('cody@gmail.com' , 'susie@gmail.com', '2022-10-12', 'sale', '10', '8'),
        ('ashley@gmail.com' , 'rudy@gmail.com', '2022-09-19', 'transfer', '5', null),
        ('rudy@gmail.com' , 'ashley@gmail.com', '2022-09-19', 'transfer', '2', null),
        ('angelo@gmail.com' , 'rudy@gmail.com', '2022-09-21', 'transfer', '2', null),
        ('todd@gmail.com' , 'cody@gmail.com', '2022-09-19', 'transfer', '10', null),
        ('susie@gmail.com' , 'sophie@gmail.com', '2022-09-22', 'transfer' ,'7', null),
        ('angelo@gmail.com' , 'todd@gmail.com', '2022-09-25', 'sale','8', '10'),
        ('jeannette@gmail.com' , 'cody@gmail.com', '2022-10-14', 'transfer', '8', null);
"

Once that has been executed you can double check it all works with:
select * from User;    
select * from Nft;
select * from Listings;
select * from Transactions;

A class is created for each table as it will be its own object, as well as a DAO for every class that allows us to insert/add/update/init() each table in the database. I will be attaching a picture that gives a rundown of the tables that are in the database. As far as part 1 goes, I did not do any of the E-R Diagram stuff at all, but if all we need to do is initialize the data then we have a huge chunk of it complete, you should make sure you can get it to work on your machine as well as change any structure you feel would improve it. I wasn't sure how he wanted us to store images for the NFTs, so right now they just link to web, but I also saved 10 nft like images in a folder in the project called images we can use if needed.
