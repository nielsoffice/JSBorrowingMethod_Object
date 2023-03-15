# JSBorrowingMethod_Object
JavaScript borrowing method in object and Object as associated of array for JS

```JS
const Developer = {
  
  /*
    Object or associated of array in JS 
    objectName : {
       objectKey1 : [ array1, values1, goes1, here1... ],
       objectKey2 : [ array2, values2, goes2, here2... ]
    }
    ACCESSING DATA IN OBJECT AS ASSOC_ARRAY :
      this.objectName.objectKey1[0]  | result is : < array1 > 
      this.objectName.objectKey2[0]  | result is : < array2 >
    --------------------------------------------------
    In PHP look like
    $array = [
       'Key1' => [ 1, 2, 3 ],
       'Key2' => [ a, b, c ]

    ];
    ACCESSING DATA IN OBJECT ARRAY :
      $array['key1'][0] | result is :  < 1 >
      $array['key2'][0] | result is :  < a >   */

    yearsExperience : {

      SKILL1 : [ 6 ],
      SKILL2 : [ 1 ]

    },
    totalExp : function() { // inCaseOf having argu: function(plus1) { ... } || function(plus1, plus2) { ... }
      // Developer.totalExp.call(Designer, 1); : return (this.yearsExperience.SKILL1[0] + this.yearsExperience.SKILL2[0]) + plus1; 
      // Developer.totalExp.call(Designer, [1, 2]); : return ((this.yearsExperience.SKILL1[0] + this.yearsExperience.SKILL2[0]) + plus1) + plus2;
      return (this.yearsExperience.SKILL1[0] + this.yearsExperience.SKILL2[0]) // without argument!
    }

}

console.log("Total Developer Experiences are : " + Developer.totalExp());

const Designer = {
  
 yearsExperience : {
    SKILL1 : [ 5 ],
    SKILL2 : [ 3 ]
 },

}

/*
  KEEP IN MIND THE BORROW METHOD ASSIGNED AND SET AS PROPERTY NOT AS FUNCTION
  ex. 
  CORRECT : Designer.totalExp = Developer.totalExp; 
  WRONG : Designer.totalExp = Developer.totalExp();
  WRONG : Designer.totalExp() = Developer.totalExp(); 
  
  EXECUTE BORROWING METHOD AS FUNCTION NOT AS PROPERTY ! 
  ex. 
  CORRECT : Designer.totalExp(); 
  WRONG : Designer.totalExp;
*/
Designer.totalExp = Developer.totalExp; 
console.log("Total Designer Experiences are : " + Designer.totalExp() );

// OR 
Developer.totalExp.call(Designer);
console.log("Total Designer Experiences are : " + Developer.totalExp.call(Designer));

// inCaseOfHaving argue: 
Developer.totalExp.call(Designer, 10 ); || Developer.totalExp.call(Designer, [10, 20] );
console.log("Total Designer Experiences are : " + Developer.totalExp.call(Designer, 10));
console.log("Total Designer Experiences are : " + Developer.totalExp.call(Designer, [10,20] ));
```
Result:

```JS
 // Console.log result 
 {yearsExperience: {…}, totalExp: ƒ}
 JS1.html:46 Total Developer Experiences are : 7
 JS1.html:40 {yearsExperience: {…}, totalExp: ƒ}
 JS1.html:58 Total Designer Experiences are : 8
 
 // Console.log Result
 // for single argument
 Total Developer Experiences are : 17 // <  7 + 10 = 17   >
 // for double arguments!
 Total Developer Experiences are : 38 // < 8 + 10 + 20 = 38  >  
```

*Prototyping Function in Object or Object inside of Object 

```JS
const staticData = {
  Property1 : [ (() => { 'ObjectValue_goes_here...' }) ]
}

// ALSO

const staticData = {
  Property1 : {
    property1A : [ (() => { 'ObjectValueA_goes_here...' }) ],
    property1B : [ (() => { 'ObjectValueB_goes_here...' }) ],
    ...
  },
  Property2 : 404,
  Property3 : 500,
  ...
}
```
