extends KinematicBody2D

var velocity = Vector2()
var speed = 200
var gravity = 500
var jump_force = -300
var is_on_ground = false

func _physics_process(delta):
    velocity.x = 0

    if Input.is_action_pressed("ui_right"):
        velocity.x += speed
    if Input.is_action_pressed("ui_left"):
        velocity.x -= speed

    if is_on_ground and Input.is_action_just_pressed("ui_up"):
        velocity.y = jump_force

    velocity.y += gravity * delta
    is_on_ground = is_on_floor()

    velocity = move_and_slide(velocity, Vector2.UP)

