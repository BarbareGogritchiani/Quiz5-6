ამ პროექტში  , გამოვიყენე  "Supermarket sales.csv" ,"Titanic-Dataset.csv" და "HousingData.csv" ფაილები. 
"HousingData.csv" - Columns
CRIM: Per capita crime rate by town.
ZN: Proportion of residential land zoned for lots over 25,000 sq. ft.
INDUS: Proportion of non-retail business acres per town.
CHAS: Charles River dummy variable (1 if tract bounds river; 0 otherwise).
NOX: Nitric oxides concentration (parts per 10 million).
RM: Average number of rooms per dwelling.
AGE: Proportion of owner-occupied units built prior to 1940.
DIS: Weighted distances to five Boston employment centers.
RAD: Index of accessibility to radial highways.
TAX: Full-value property tax rate per $10,000.
PTRATIO: Pupil-teacher ratio by town.
B: 1000(Bk - 0.63)^2 where Bk is the proportion of Black residents by town.
LSTAT: Percentage of lower status of the population.
MEDV: Median value of owner-occupied homes in $1000s.
ფაილი გავხსენი , მასში არსებული NaN მონაცემები შევცვალე საშუალო მნიშვნელობებით , ამოვიღეთ სვეტი PTRATIO , რომელიც გვაწვდის ინფორმაციას განათლების დონესთან დაკავშირებით კონკრეტულ არეაზე . რაც უფრო დაბალია ის , მით უკეთესია განათლების ხარისხის მაჩვენებლი . შემდეგ დავყავი სატესტო მონაცემებად X , y სადაც X არის ცხრილი ამ სვეტის გარეშე , ხოლო y თავად სვეტი . Linear Regression - ის  საშუალებით დავადგინეთ R2 score ,, რომელიც დაახლოებით  0.392-ის ტოლია , რაც ნიშნავს , რომ დაახლოებით 39,2% -ით მქომედებს ცხრილში წარმოდგენილი ფაქტორები PTRATIO -ზე მ ხოლო 60.8% ით არ ახდენს ის გავლენას და შესაძლოა არსებობდეს სხვა ფაქტორები, რომლებიც არაა წარმოდგენილი ცხრილში და მოქმედებს მის მნიშვნელობაზე . 
"supermarketsales.csv" - Columns 
Invoice ID: Unique identifier for each invoice.
Branch: Branch identifier (e.g., A, B, C).
City: City where the branch is located.
Customer type: Type of customer (e.g., Member, Normal).
Gender: Gender of the customer (e.g., Male, Female).
Product line: Product category (e.g., Health and beauty, Electronic accessories).
Unit price: Price per unit of the product.
Quantity: Quantity of products purchased.
Tax 5%: Tax amount (5% of the total).
Total: Total amount paid, including tax.
Date: Date of the transaction.
Time: Time of the transaction.
Payment: Payment method (e.g., Cash, Credit card, Ewallet).
COGS: Cost of goods sold.
Gross margin percentage: Gross margin percentage.
Gross income: Gross income from the transaction.
Rating: Customer satisfaction rating.
წარმოვადგინე X , რომელშიც არის 'Unit price', 'Quantity', 'Tax 5%', 'Total' სვეტები  და  y , რომელშიც არის 'Total' სვეტი . კვლავ დავყავი სატესტო მონაცემებად  და მრავალცვლადიანი რეგრესიის მოდელის გამოყენებით დავთვალეთ R2 score , რომელიც ამ შემთხვევაში 1-ის ტოლია , ეს ნიშNავს , რომ წარმოდგენილი სვეტების საშუალებით ზუსტადაა შესაძლებელი Total სვეტის განსაზღვრა . (100% სიზუსტით ) ხოლო იგივე შემთხვევაში გადაწყვეტილების ხის საშუალებით გვაქვს 'Unit price', 'Quantity', 'cogs' სვეტების გავლენა 99.9% სიზუსტით 
'Titanic-Dataset.csv'-columns 
PassengerId: Unique identifier for each passenger.
Survived: Survival status of the passenger (0 = No, 1 = Yes).
Pclass: Ticket class (1 = 1st, 2 = 2nd, 3 = 3rd).
Name: Passenger's name.
Sex: Passenger's gender.
Age: Passenger's age.
SibSp: Number of siblings/spouses aboard the Titanic.
Parch: Number of parents/children aboard the Titanic.
Ticket: Ticket number.
Fare: Passenger fare.
Cabin: Cabin number.
Embarked: Port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton).
ამოვიღეთ არასაჭირო სვეტები ['Cabin', 'Ticket', 'Name'] , შემდეგი  სვეტების თითოეული ელემენტი/მნიშვნელობა გადავაქციეთ რიცხვით მონაცემად map()-ის გამოყენებით 
df_2['Sex'] = df_2['Sex'].map({'male': 0, 'female': 1})
df_2['Embarked'] = df_2['Embarked'].map({'S': 0, 'C': 1, 'Q': 2}) 
Age სვეტში გამოტოვებული ადგილები საშუალო მნიშვნელობით შევავსეთ და მოდით შევავსეთ Embarked სვეტში არსებული გამოტოვებული ადგილები . დავყავით სატესტი მონაცემმებად და ლოგისტიკური რეგრესიის მოდელის საშუალებით განვსაზღვრეთ , რომ დაახლოებით 79% ითაა შესაძ₾ებელი განსაზღვრა მგზავრი გადარჩება თუ არა წარმოდგენილი მონაცემების მიხედვით(PassengerId	Pclass	Sex	Age	SibSp	Parch	Fare	Embarked) 
საბოლოოდ ისევ სუპერმარკეტის გაყიდვების შესახებ ცხრილი წარმოვადგინე , საიდანაც წავშალეთ ზედმეტი მონაცემები ('Invoice ID', 'Branch', 'Customer type', 'Gender', 'Payment', 'Date', 'Time')
LabelEncoder() -ის საშუალებით წარმოვადგინეთ 2 მახასიათებელი city ,product line , რომელთა გავლენაც უნდა განვსაზღვროთ Rating Category_ზე , შედეგად მივიღეთ 74% სიზუსტე 
