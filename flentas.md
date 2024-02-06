call_log = [
["9898989898", "8989898989", "00:05:23"],
["1898989898", "9989898989", "01:00:23"],
["2898989898", "7989898989", "00:00:21"],
["2898989898", "6989898989", "00:00:23"],
["4898989898", "5989898989", "00:01:23"],
["5898989898", "4989898989", "00:05:55"],
["5898989898", "3989898989", "00:00:23"],
["7898989898", "2989898989", "00:02:23"],
["8898989898", "1189898989", "00:05:20"],
["1098989898", "8459898989", "00:00:23"],
["1898989898", "8967898989", "00:00:40"],
["2898989898", "8989898989", "00:05:23"],
]
distinct_from_numbers = set()
free_plan_users = set()
call_duration_by_number = {}
total_income = 0
for call in call_log:
from_number, to_number, call_duration = call
distinct_from_numbers.add(from_number)
call_duration_parts = call_duration.split(':')
total_minutes = int(call_duration_parts[0]) * 60 + int(call_duration_parts[1])
if total_minutes < 1:
free_plan_users.add(from_number)
else:
cost = (total_minutes - 1) * 0.30 # Deducting 1st minute as it's free
total_income += cost
call_duration_by_number[from_number] = call_duration_by_number.get(from_number, 0) +
total_minutes
print("Distinct From Numbers for a day:", distinct_from_numbers)
print("Distinct From Numbers who used the Free Plan:", free_plan_users)
print("Total call duration with respect to From Number:")
for from_number, duration in call_duration_by_number.items():
print(f"{from_number}: {duration} minutes")
print("Total income for a day (in paise):", int(total_income))
