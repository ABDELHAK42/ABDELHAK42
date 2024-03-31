import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import java.util.List;

public class MainActivity extends AppCompatActivity {

    private DidouFit didouFit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        didouFit = new DidouFit();
        didouFit.addWorkout(new Workout("Bench Press", 4, 10));
        didouFit.addWorkout(new Workout("Squats", 5, 8));
        didouFit.addWorkout(new Workout("Deadlifts", 4, 6));

        displayWorkouts();
    }

    private void displayWorkouts() {
        List<Workout> workouts = didouFit.getWorkouts();
        TextView textView = findViewById(R.id.textView);

        StringBuilder stringBuilder = new StringBuilder();
        for (Workout workout : workouts) {
            stringBuilder.append(workout.getName())
                    .append(" - Sets: ").append(workout.getSets())
                    .append(", Reps: ").append(workout.getReps())
                    .append("\n");
        }

        textView.setText(stringBuilder.toString());
    }
}
