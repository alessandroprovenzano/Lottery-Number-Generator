
from random import choice

def input_number(prompt, min_value, max_value):
	value = None
	while value is None:
		try:
			value = int(input(prompt))
		except ValueError:
			print('Please enter a number!')
		if value < min_value or value > max_value:
			print('Please enter a number between %i and %i!' % 
			       (min_value, max_value))
			value = None
	return value

title = 'Lottery Number Generator'
print(title)
print('=' * 40)
minimum = input_number('Smallest number: ', 1, 9999)
maximum = input_number('Largest number: ', minimum, 9999)
n = input_number('How many numbers do you want to draw? ', 
                 1, maximum - minimum + 1)

all_numbers = list(range(minimum, maximum + 1))
selection = []
for i in range(n):
	r = choice(all_numbers)
	selection.append(r)
	all_numbers.remove(r)
print('=' * 40)
print('Your numbers:', selection)
