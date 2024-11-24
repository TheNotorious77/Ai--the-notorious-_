# commute_decision.py

def get_commute_mode(distance, time_available, weather, preference):
    """
    Suggests the best mode of transportation for your commute.
    
    Parameters:
    - distance: float, distance in kilometers.
    - time_available: float, time available in minutes.
    - weather: str, "sunny", "rainy", "snowy", or "cloudy".
    - preference: str, "eco", "fast", or "comfortable".
    
    Returns:
    - str, suggested commute mode.
    """
    if weather.lower() == "rainy" or weather.lower() == "snowy":
        if preference == "comfortable":
            return "Take a car or taxi."
        else:
            return "Use public transport (bus/train)."
    elif distance < 2:
        if time_available > 20 and preference == "eco":
            return "Walk."
        else:
            return "Ride a bicycle."
    elif distance <= 10:
        if time_available < 30 or preference == "fast":
            return "Use a motorcycle or e-scooter."
        else:
            return "Ride a bicycle."
    else:
        if preference == "fast":
            return "Drive or use a taxi."
        elif preference == "eco":
            return "Take public transport."
        else:
            return "Drive or carpool."

def main():
    print("Welcome to Commute Decision Helper!")
    try:
        distance = float(input("Enter the distance to your destination (in kilometers): "))
        time_available = float(input("Enter the time you have for the commute (in minutes): "))
        weather = input("Enter the current weather (sunny/rainy/snowy/cloudy): ").strip().lower()
        preference = input("What do you prioritize? (eco/fast/comfortable): ").strip().lower()

        result = get_commute_mode(distance, time_available, weather, preference)
        print(f"Suggested commute mode: {result}")
    except ValueError:
        print("Invalid input. Please enter numbers for distance and time.")

if __name__ == "__main__":
    main()# Ai--the-notorious-_
    How it Works:

1. User Input:

Distance to the destination.

Available time for the commute.

Current weather.

Personal preference (eco, fast, or comfortable).



2. Decision Making:

Uses conditional logic to suggest walking, biking, public transport, or driving based on inputs.



3. Output:

Suggests the most suitable commute mode.
