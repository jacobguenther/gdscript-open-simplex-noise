# OpenSimplex Noise in GDScript

## The API

setNewSeed(int):
	Rebuild the permutations array using the built in psudo random number geneartor

eval2D(float x, float y)
	Returns the noise value at a postion (x, y)

eval3D(float x, float y, float z)
	Returns the noise value at a position (x, y, z)

eval4D(float x, float y, float z, float w)
	Return the noise value at a position (x, y, z, w)


## Example Usage

Generating a texture using 2D OpenSimplex noise

- Create a node with the code in it below.
- Attach OpenSimplexNoise.gd to a child node and run the scene

'''
	var size = 128
	var pathToImage = "res://noise.png"
	var featureSize = 24.0
	
	var rawData = PoolByteArray()
	var noise
	var value
	for x in range(0, size):
		for y in range(0, size):
			noise = $OpenSimplexNoise.eval2D(x / featureSize, y / featureSize)
			value = inverse_lerp(-1, 1, noise)*255
			print(noise, " ", value)
			rawData.append(value)
			rawData.append(value)
			rawData.append(value)
	
	var image = Image.new()
	image.create_from_data(size, size, false, 4, rawData)
	image.save_png(pathToImage)
'''





