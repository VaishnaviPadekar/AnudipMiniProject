import getpass

print("🔐 Password Strength Checker")

password = getpass.getpass("Enter your password: ")

score = 0
suggestions = []

# Length check
if len(password) >= 8:
    score += 1
else:
    suggestions.append("Use at least 8 characters")

# Uppercase
if any(ch.isupper() for ch in password):
    score += 1
else:
    suggestions.append("Add uppercase letter")

# Lowercase
if any(ch.islower() for ch in password):
    score += 1
else:
    suggestions.append("Add lowercase letter")

# Digit
if any(ch.isdigit() for ch in password):
    score += 1
else:
    suggestions.append("Add a number")

# Special character
if any(not ch.isalnum() for ch in password):
    score += 1
else:
    suggestions.append("Add special character (@, #, $)")

# Strength result
print("\n🔎 Password Analysis:")

if score == 5:
    print("Strength: VERY STRONG 💪")
elif score >= 3:
    print("Strength: MEDIUM 🙂")
else:
    print("Strength: WEAK 😐")

print("Score:", score, "/ 5")

# Suggestions
if suggestions:
    print("\n⚠ Suggestions to improve:")
    for s in suggestions:
        print("-", s)
else:
    print("\n✅ Perfect Password!")
