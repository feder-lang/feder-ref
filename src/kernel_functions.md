## Functions

### Floating-point

```
use module std

/**@return Returns true, if float is a special IEEE-754 value.
 */
func@Safe isSpecialFloat(float32) : bool;

/**@return Returns true, if float is a special IEEE-754 value.
 */
func@Safe isSpecialFloat(float64) : bool;

/**@return Returns true, if float is a special IEEE-754 value.
 */
func@Safe,Unique isSpecialFloat32(float32) : bool;

/**@return Returns true, if float is a special IEEE-754 value.
 */
func@Safe,Unique isSpecialFloat64(float64) : bool;

/** Terminates program.
 */
func@Safe panic ;
```
