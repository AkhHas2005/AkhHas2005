# Android studio missing import dialog interface  

## Me
This is my code but I'm missing the import for the dialog interface and can't find it:  

```Java
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
        EditText num1 = findViewById(R.id. editNo1);
        EditText    num2 = findViewById(R.id. editNo2);

        TextView result = findViewById(R.id. result);

        Button button = findViewById(R.id.button);

        button.setOnClickListener(new DialogInterface.OnClickListener() {
            @Override
            public void onClick(View v) {

                double numb1 = Double.parseDouble(num1.getText().toString());
                double numb2 = Double.parseDouble(num2.getText().toString());
                double res= numb1 + numb2;
                result.setText(String.format("%.2f", new BigDecimal(res)));

            }
        });
    }  
```

## Co-Pilot
You're right to look for the correct import—your code is currently using `new DialogInterface.OnClickListener()` inside a Button's `setOnClickListener`, which is **not appropriate** for button clicks.  

### ✅ Here's the fix:  

You should use `View.OnClickListener` instead of `DialogInterface.OnClickListener`. The latter is meant for dialog buttons (like in `AlertDialog`), not regular UI buttons.  

### ✅ Corrected code snippet:  

```Java
button.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        double numb1 = Double.parseDouble(num1.getText().toString());
        double numb2 = Double.parseDouble(num2.getText().toString());
        double res = numb1 + numb2;
        result.setText(String.format("%.2f", new BigDecimal(res)));
    }
});
```

### ✅ Required import:  

Make sure you have this import at the top of your Java file:  

```Java
import android.view.View;
```  

Let me know if you're planning to use a dialog later—then `DialogInterface.OnClickListener` would make sense. Want help adding a confirmation dialog before showing the result?    

*End of this Conversation*
