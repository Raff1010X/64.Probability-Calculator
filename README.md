# [freeCodeCamp Scientific Computing with Python](https://www.freecodecamp.org/learn/scientific-computing-with-python)

## [Probability-Calculator](https://www.freecodecamp.org/learn/scientific-computing-with-python/scientific-computing-with-python-projects/probability-calculator)

My git repo: https://github.com/Raff1010X/01.Roadmap

```python
import copy
import random

class Hat:
    def __init__(self, **balls):
        self.contents = sum(map(lambda item: [item[0]] * item[1], balls.items()), [])

    def draw(self, number):
        if number >= len(self.contents):
            content = self.contents
            self.contents = []
            return content
        else:
            selected = random.sample(self.contents, number)
            for element in selected:
                self.contents.remove(element)
            return selected
       
def experiment(**args):
    hat = args['hat']
    expected_balls = args['expected_balls']
    num_balls_drawn = args['num_balls_drawn']
    num_experiments = args['num_experiments']
    match = 0
    for index in range(num_experiments):
        hat_copy = copy.deepcopy(hat)
        # while len(hat_copy.contents) > 0: # for multiple draw from hat add indent below before return
        drawed = hat_copy.draw(num_balls_drawn)
        if all(drawed.count(color) >= expected_balls[color] for color in expected_balls):
            match += 1
    return match / num_experiments

# test
hat = Hat(black=6, red=4, green=3)
probability = experiment(hat=hat,
                  expected_balls={"red":2,"green":1},
                  num_balls_drawn=5,
                  num_experiments=2000)

print(probability)
```
