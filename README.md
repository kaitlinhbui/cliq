import simplegui

class ShapeAttributes:

    def __init__(self):
        self.line_width = 5
        self.line_color = "Blue"
        self.fill_color = "Orange"
    
    
class Circle:

    def __init__(self):
        self.radius = 50
        self.center_point = (100, 100)
        
    def update_x(self, shift_x):
        self.center_point = (
            self.center_point[0] + shift_x,
            self.center_point[1]
        )
        
    def update_y(self, shift_y):
        self.center_point = (
            self.center_point[0],
            self.center_point[1] + shift_y
        )
class Character:
    
    key_map = {
            "right": 39,
            "left": 37,
            "up": 38,
            "down": 40
        }
    
    movement = 10
    
    def __init__(self):
        self.circle_shape = Circle()
        self.circle_attributes = ShapeAttributes()

    def draw_me(self, canvas):
        canvas.draw_circle(self.circle_shape.center_point, self.circle_shape.radius, self.circle_attributes.line_width, self.circle_attributes.line_color, self.circle_attributes.fill_color)
        canvas.draw_circle(self.circle_shape.center_point, 30, 3, 'White', 'White')
        canvas.draw_circle(self.circle_shape.center_point, 15, 3, 'Yellow', 'Yellow')

    def move(self, key):
        if key == 39:
            self.circle_shape.update_x(self.movement)
        if key == 37:
            self.circle_shape.update_x(-self.movement)
        if key == 40:
            self.circle_shape.update_y(self.movement)
        if key == 38:
            self.circle_shape.update_y(-self.movement)
        print key
        
cliq = Character()

#Handler to draw on canvas

def draw(canvas): cliq.draw_me(canvas)

#Create a frame and assign callbacks to event handlers

frame = simplegui.create_frame("Home", 500, 500)


#Start the frame animation
frame.set_draw_handler(draw)
frame.set_keydown_handler(cliq.move)
frame.start()
    
    
    
    
    
