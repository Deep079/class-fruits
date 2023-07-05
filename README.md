from flask import Flask, jsonify

app = Flask(_name_)

class Fruit:
    def _init_(self, id, name, color):
        self.id = id
        self.name = name
        self.color = color

# Sample data
fruits = [
    Fruit(1, 'Apple', 'Red'),
    Fruit(2, 'Banana', 'Yellow'),
    Fruit(3, 'Orange', 'Orange'),
    Fruit(4, 'Grapes', 'Purple'),
    Fruit(5, 'Watermelon', 'Green'),
]

@app.route('/fruits', methods=['GET'])
def get_sorted_fruits():
    sorted_fruits = sorted(fruits, key=lambda x: x.color)
    fruit_list = [{'id': fruit.id, 'name': fruit.name, 'color': fruit.color} for fruit in sorted_fruits]
    return jsonify(fruit_list)

if _name_ == '_main_':
    app.run()
