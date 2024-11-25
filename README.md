# Cylinder-Volume-Calculation-Using-Python-and-LLM-Integration

## AIM:
To develop a Python-based system that calculates the volume of a cylinder and integrates it with a chat-like interaction system using a function-calling mechanism, allowing users to provide input in natural language queries.

## ALGORITHM:
STEP 1: Define the Cylinder Volume Function:
Create a function calculate_cylinder_volume(radius, height) that uses the formula
Validate that radius and height are non-negative.

STE 2: Process the User Query:
Accept a natural language query from the user (e.g., "What is the volume of a cylinder with radius 5 and height 10?").
Clean the query by removing unnecessary characters (e.g., ?).

STEP 3: Extract Parameters:
Parse the query to identify radius and height.
Convert the extracted values into floating-point numbers.

STEP 4: Validate Parameters:
Ensure both radius and height are valid and non-negative.
Handle any errors if the parameters are missing or invalid.

STEP 5: Calculate the Volume:
Pass the extracted radius and height to calculate_cylinder_volume.
Compute and return the volume.

STEP 6: Respond to the User:
Format the output as a user-friendly response.
Handle errors gracefully and inform the user about invalid input.

STEP 7: Simulate the Interaction:
Combine all steps into a chat-like interaction where the system responds based on user input.

## PROGRAM:
```
Developed by: SADHANA SHREE B
Register Number: 212223230177

import math
import json

# Function to calculate the volume of a cylinder
def calculate_cylinder_volume(radius: float, height: float) -> float:
    if radius < 0 or height < 0:
        raise ValueError("Radius and height must be non-negative.")
    return math.pi * (radius ** 2) * height


# Function schema for LLM integration
function_definition = {
    "name": "calculate_cylinder_volume",
    "description": "Calculates the volume of a cylinder given its radius and height.",
    "parameters": {
        "type": "object",
        "properties": {
            "radius": {"type": "number", "description": "Radius of the cylinder."},
            "height": {"type": "number", "description": "Height of the cylinder."},
        },
        "required": ["radius", "height"],
    },
}


# Simulate user query parsing and interaction
def simulate_llm_interaction(user_query: str):
    # Clean the query by removing special characters like '?'
    cleaned_query = user_query.replace("?", "")
    
    # Mocked parameter extraction (LLM processing would be dynamic in real applications)
    if "radius" in cleaned_query and "height" in cleaned_query:
        try:
            # Extract radius and height from the query
            words = cleaned_query.split()
            radius = float(words[words.index("radius") + 1])
            height = float(words[words.index("height") + 1])
            
            # Call the function
            volume = calculate_cylinder_volume(radius=radius, height=height)
            
            # Return a user-friendly response
            return {"response": f"The volume of the cylinder is {volume:.2f} cubic units."}
        except ValueError as ve:
            return {"error": f"Invalid input: {ve}"}
        except Exception as e:
            return {"error": f"An error occurred: {e}"}
    else:
        return {"error": "Please provide both radius and height in the query."}


# Example usage
if __name__ == "__main__":
    # Simulated user input
    user_query = "What is the volume of a cylinder with radius 5 and height 10?"

    # Simulate the interaction
    response = simulate_llm_interaction(user_query)

    # Print the response
    print(json.dumps(response, indent=2))
```

## OUTPUT:
![Screenshot 2024-11-25 113258](https://github.com/user-attachments/assets/e0cfd9be-18ce-41b0-8ef2-7e33c34b48a2)

## RESULT:
Thus, the aim of creating a Python-based system to calculate the volume of a cylinder through user queries has been successfully achieved.
