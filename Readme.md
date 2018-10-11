# Welcome.
This is where some highlights of coding assignments from [Ada Developers Academy's Jump Start](https://github.com/Ada-Developers-Academy/jump-start) lessons will live.

## Account Generator (Hashes)
This is my code for the [Account Generator Continued assignment](https://github.com/Ada-Developers-Academy/jump-start/blob/master/learning-to-code/hashes/assignments/account-generator-cont.md) from the Hashes lesson (includes commentary and explanations). The code is refactored from the first version of the assignment, [Account Generator](https://github.com/Ada-Developers-Academy/jump-start/blob/master/learning-to-code/arrays/assignments/account-generator.md). My code for that assignment is [below](https://github.com/evelynnkaplan/AdaJumpstart#account-generator-arrays).

```#Define empty array. This array will store all of the hashes with student info.
student_info = []
#Utilize a single loop to drive the population of the array with the hashes containing info for 5 students. 
5.times do
  #Add an empty hash for each individual student's information.
  student = {} 
  #Start filling up the array. Accept user input for student name. I chose to keep first and last name input separate, 
  #because later I will need to use only a slice of the first name but the whole last name. Accepting separate user input 
  #for the last name means I can access the last name without having to know how many characters are in the last name. 
  #There are other ways to access only the last name, even if the last name is in the same string as the first name 
  #(such as using the split method), but I think that having the last name be a separate, defined variable is the simplest solution here.
  puts "Please type your first name."
  first = gets.chomp.upcase
  puts "Please type your last name."
  last = gets.chomp.upcase
  #Add this input to the hash, assigning the input as the value to the key "name."
  student["name"] = first + " " + last 
  #Generate random numbers from 111111 to 999999 for each student. These will be used for the student ID numbers. 
  #Assign the random ID number as the value for the key "id." Later I will need to use the slice method on the ID number, 
  #so convert the random integer output to a string now. The slice method can only be used on a string.
  student["id"] = rand(111111..999999).to_s
  #Generate student email addresses. Email address will contain first letter of first name,full last name, 
  #and last 3 digits of student id number, plus "@adadevelopersacademy.org." The slice method is used to access 
  #the student's first initial as well as the last three digits of the student's ID number.
  student["email"] = first.slice(0) + last + student["id"].slice(3..5) + "@adadevelopersacademy.org"
  #Add hash with all of the student's info to the array.
  student_info << student 
end
#Add a line break for better visual readability.
puts 
#Print the student roster.
5.times do |n|
  puts "Name: " + student_info[n]["name"]
  puts "ID number: " + student_info[n]["id"]
  puts "Email address: " + student_info[n]["email"]
  #Add a line break for better visual readability.
  puts 
end
```

## Account Generator (Arrays)
This is my code for the [Account Generator assignment](https://github.com/Ada-Developers-Academy/jump-start/blob/master/learning-to-code/arrays/assignments/account-generator.md) from the Arrays lesson (includes a bit of commentary). 

```#Define arrays.
names = []
ids = []
emails = []

#Ask user for their first and last name and put the two names together in a string.
5.times do |n|
  puts "Please type your first name."
  first = gets.chomp.upcase
  puts "Please type your last name."
  last = gets.chomp.upcase
  names.push "#{first} "  + last
#Generate random numbers from 111111 to 999999 for each student. 
#These will be used for the student ID numbers. 
 ids.push(rand(111111..999999))
#Convert the ID numbers from integers into strings, 
#because integers cannot be split but strings can. Each id number will need 
#to be split in order to use the last three digits for the email address.
 ids[n] = ids[n].to_s 
  emails << first.slice(0) + last + ids[n].slice(3..5) + "@adadevelopersacademy.org"
end
final = emails.join(" ")
print final
``` 

## Election Time
This is my code for the [Election Time](https://github.com/Ada-Developers-Academy/jump-start/blob/master/learning-to-code/iterators/assignments/election.md) assignment from the Iterators lesson. I had a lot of fun with this one!

```puts "It's the first Tuesday in November, so you know what that means. Election time! But because Evelynn already is in charge of this domain, you're voting on breakfast foods. There's no wrong answer, but there can (hopefully) only be one winner."
puts "\n"
puts "Cast your vote for one of the following: waffles, eggs, pancakes, or tacos."
puts "\n"
puts "Yes, I said tacos. Have you ever had breakfast tacos?"
puts "\n"
waffles = 0
eggs = 0
pancakes = 0
tacos = 0
while waffles + eggs + pancakes + tacos < 10
  puts "Spelling matters in this election! What are you voting for?"
  vote = gets.chomp.downcase 
  if vote == "waffles"
    waffles += 1
  elsif vote == "eggs"
    eggs += 1
  elsif vote == "pancakes"
    pancakes += 1
  elsif vote == "tacos"
    tacos += 1
  else
    puts "I'm sorry, I won't accept a write-in vote or a misspelled vote. Your vote has not been totaled."
  end
end
puts "\n"
puts "Thank you for doing your duty as a citizen! Local breakfast food elections matter." 
puts "Here are the results:"
puts "\n"
puts "Waffles: #{waffles}"
puts "Eggs: #{eggs}"
puts "Pancakes: #{pancakes}"
puts "Tacos: #{tacos}"
puts "\n"
puts "And the winner is........"
if (waffles > eggs) && (waffles > pancakes) && (waffles > tacos)
  puts "Waffles!"
elsif (eggs > waffles) && (eggs > pancakes) && (eggs > tacos)
  puts "Eggs!"
elsif (pancakes > waffles) && (pancakes > eggs) && (pancakes > tacos)
  puts "Pancakes!"
elsif (tacos > waffles) && (tacos > pancakes) && (tacos > eggs)
  puts "Tacos!"
elsif (waffles == pancakes) || (waffles == eggs) || (waffles == tacos) || (pancakes == eggs) || (pancakes == tacos) || (eggs == tacos)
  if (waffles >= 3)
    if (pancakes >= 3)
      puts "Tie between waffles and pancakes. That's fine, you can eat both."
    elsif (eggs >= 3)
      puts "Tie between waffles and eggs. That's fine, you can eat both."
    else
      puts "Tie between waffles and tacos. That's fine, you can eat both."
    end
  elsif (pancakes >= 3)
    if (eggs >= 3)
      puts "Tie between eggs and pancakes. That's fine, you can eat both."
    else 
      puts "Tie between pancakes and tacos. That's fine, you can eat both."
    end
  else 
    puts "Tie between eggs and tacos. That's fine, you can eat both."
  end
end
```
