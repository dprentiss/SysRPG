numRooms = 16
rooms = []

var lcg = (function() {
  // Set to values from http://en.wikipedia.org/wiki/Numerical_Recipes
      // m is basically chosen to be large (as it is the max period)
      // and for its relationships to a and c
  var m = 4294967296,
      // a - 1 should be divisible by m's prime factors
      a = 1664525,
      // c and m should be co-prime
      c = 1013904223,
      seed, z;
  return {
    setSeed : function(val) {
      z = seed = val || Math.round(Math.random() * m);
    },
    getSeed : function() {
      return seed;
    },
    rand : function() {
      // define the recurrence relationship
      z = (a * z + c) % m;
      // return a float in [0, 1) 
      // if z = m then z / m = 0 therefore (z % m) / m < 1 always
      return z / m;
    }
  };
}());

function normal_random(mean, variance) {
  if (mean == undefined)
    mean = 0.0;
  if (variance == undefined)
    variance = 1.0;
  var V1, V2, S;
  do {
    var U1 = lcg.rand();
    var U2 = lcg.rand();
    V1 = 2 * U1 - 1;
    V2 = 2 * U2 - 1;
    S = V1 * V1 + V2 * V2;
  } while (S > 1);

  X = Math.sqrt(-2 * Math.log(S) / S) * V1;
//Y = Math.sqrt(-2 * Math.log(S) / S) * V2;
  X = mean + Math.sqrt(variance) * X;
//Y = mean + Math.sqrt(variance) * Y ;
  return X;
}

var Room = function(mu, sigma, radius) {
	this.height = 0;
}

lcg.setSeed(0);

for(i = 0; i < numRooms; i += 1) {
	rooms.push({
		height: Math.round(normal_random(10, 5)),
		width: Math.round(normal_random(10, 5)),
		x: Math.round(normal_random(0, 50)),
		y: Math.round(normal_random(0, 50))})
}

console.log(rooms)
