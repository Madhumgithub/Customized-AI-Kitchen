class AIKitchen:
    def __init__(self):
        self.recipes = self.load_recipes()
        self.substitutions = self.load_substitutions()
        self.tips = self.load_tips()

    def load_recipes(self):
        return {
            "Chole": ["chickpeas", "onions", "tomatoes", "garam masala"],
            "Palak Paneer": ["spinach", "paneer", "cream", "onions"],
            "Biryani": ["rice", "chicken", "yogurt", "saffron"],
            "Aloo Gobi": ["potatoes", "cauliflower", "tomatoes", "spices"]
        }

    def load_substitutions(self):
        return {
            "paneer": "tofu",
            "yogurt": "coconut milk",
            "cream": "cashew paste",
            "ghee": "oil"
        }

    def load_tips(self):
        return [
            "To enhance flavors, roast spices before grinding.",
            "Always soak lentils and beans to reduce cooking time.",
            "Use fresh herbs like coriander and mint for garnish to add a fresh flavor.",
            "Balance the heat of spicy dishes with a dollop of yogurt or a squeeze of lime."
        ]

    def recommend_recipes(self, ingredients):
        available_recipes = []
        for recipe, required_ingredients in self.recipes.items():
            if all(ingredient in ingredients for ingredient in required_ingredients):
                available_recipes.append(recipe)
        return available_recipes

    def suggest_substitutions(self, missing_ingredients):
        return {ingredient: self.substitutions.get(ingredient, "No substitution available") for ingredient in missing_ingredients}

    def get_cooking_tips(self):
        return self.tips

# Example usage
kitchen_assistant = AIKitchen()

# User has these ingredients
user_ingredients = ["chickpeas", "onions", "tomatoes", "garam masala", "spinach", "paneer"]

# Recommend recipes based on available ingredients
recommended_recipes = kitchen_assistant.recommend_recipes(user_ingredients)
print("Recommended Recipes:", recommended_recipes)

# User is missing these ingredients
missing_ingredients = ["yogurt", "cream"]
substitutions = kitchen_assistant.suggest_substitutions(missing_ingredients)
print("Ingredient Substitutions:", substitutions)

# Get cooking tips
cooking_tips = kitchen_assistant.get_cooking_tips()
print("Cooking Tips:", cooking_tips)
