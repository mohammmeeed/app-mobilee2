# app-mobilee2

package com.example.map_habltnii;

import androidx.fragment.app.FragmentActivity;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.ScaleAnimation;
import android.widget.ImageView;
import android.widget.LinearLayout;
import android.widget.TextView;

import com.google.android.gms.maps.CameraUpdateFactory;
import com.google.android.gms.maps.GoogleMap;
import com.google.android.gms.maps.OnMapReadyCallback;
import com.google.android.gms.maps.SupportMapFragment;
import com.google.android.gms.maps.model.LatLng;
import com.google.android.gms.maps.model.MarkerOptions;
import com.example.map_habltnii.databinding.ActivityMapsBinding;

public class MapsActivity extends FragmentActivity implements OnMapReadyCallback {

    private GoogleMap mMap;
    private ActivityMapsBinding binding;
private int selecttable = 1 ;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        binding = ActivityMapsBinding.inflate(getLayoutInflater());
        setContentView(binding.getRoot());

        // Obtain the SupportMapFragment and get notified when the map is ready to be used.
        SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
                .findFragmentById(R.id.map);
        mapFragment.getMapAsync(this);
        final LinearLayout layouthome = findViewById(R.id.layouthome);
        final LinearLayout layoutticket = findViewById(R.id.layoutticket);
        final LinearLayout layoutmenu = findViewById(R.id.layoutmenu);
        final ImageView iconhome = findViewById(R.id.iconhome);
        final ImageView iconticket = findViewById(R.id.iconticket);
        final ImageView iconmenu = findViewById(R.id.iconmenu);
        final TextView texthome = findViewById(R.id.texthome);
        final TextView textticket = findViewById(R.id.textticket);
        final TextView textmenu = findViewById(R.id.textmenu);

        getSupportFragmentManager().beginTransaction()
                .setReorderingAllowed(true)
                .replace(R.id.fragmentcontainer,MapsFragment.class,null)
                .commit();





        layouthome.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (selecttable != 1){
                    getSupportFragmentManager().beginTransaction()
                            .setReorderingAllowed(true)
                            .replace(R.id.fragmentcontainer,MapsFragment.class,null)
                            .commit();
                    textticket.setVisibility(View.GONE);
                    textmenu.setVisibility(View.GONE);

                    iconticket.setImageResource(R.drawable.baseline_map_24);
                    iconmenu.setImageResource(R.drawable.baseline_map_24);

                    layoutticket.setBackgroundColor(getColor(android.R.color.transparent));
                    layoutmenu.setBackgroundColor(getColor(android.R.color.transparent));

                    texthome.setVisibility(View.VISIBLE);
                    iconhome.setImageResource(R.drawable.baseline_map_24);
                    layouthome.setBackgroundColor(R.drawable.roundhome);

                    ScaleAnimation ScaleAnimation = new ScaleAnimation(0.8f,1.0f,1f,1f, Animation.RELATIVE_TO_SELF,1.0f,Animation.RELATIVE_TO_SELF,0.0f);
                    ScaleAnimation.setFillAfter(true);
                    layouthome.startAnimation(ScaleAnimation);


                    selecttable = 1;
                }

            }
        });


        layoutticket.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (selecttable != 2){
                    getSupportFragmentManager().beginTransaction()
                            .setReorderingAllowed(true)
                            .replace(R.id.fragmentcontainer,ticket_fragment.class,null)
                            .commit();
                    texthome.setVisibility(View.GONE);
                    textmenu.setVisibility(View.GONE);

                    iconhome.setImageResource(R.drawable.baseline_map_24);
                    iconmenu.setImageResource(R.drawable.baseline_map_24);

                    layouthome.setBackgroundColor(getColor(android.R.color.transparent));
                    layoutmenu.setBackgroundColor(getColor(android.R.color.transparent));

                    textticket.setVisibility(View.VISIBLE);
                    iconticket.setImageResource(R.drawable.baseline_map_24);
                    layoutticket.setBackgroundColor(R.drawable.roundhome);

                    ScaleAnimation ScaleAnimation = new ScaleAnimation(0.8f,1.0f,1f,1f, Animation.RELATIVE_TO_SELF,1.0f,Animation.RELATIVE_TO_SELF,0.0f);
                    ScaleAnimation.setFillAfter(true);
                    layoutticket.startAnimation(ScaleAnimation);


                    selecttable = 2;
                }


            }
        });



        layoutmenu.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (selecttable != 3){
                    getSupportFragmentManager().beginTransaction()
                            .setReorderingAllowed(true)
                            .replace(R.id.fragmentcontainer,menu_page.class,null)
                            .commit();
                    textticket.setVisibility(View.GONE);
                    texthome.setVisibility(View.GONE);

                    iconticket.setImageResource(R.drawable.baseline_map_24);
                    iconhome.setImageResource(R.drawable.baseline_map_24);

                    layoutticket.setBackgroundColor(getColor(android.R.color.transparent));
                    layouthome.setBackgroundColor(getColor(android.R.color.transparent));

                    textmenu.setVisibility(View.VISIBLE);
                    iconmenu.setImageResource(R.drawable.baseline_map_24);
                    layoutmenu.setBackgroundColor(R.drawable.roundhome);

                    ScaleAnimation ScaleAnimation = new ScaleAnimation(0.8f,1.0f,1f,1f, Animation.RELATIVE_TO_SELF,1.0f,Animation.RELATIVE_TO_SELF,0.0f);
                    ScaleAnimation.setFillAfter(true);
                    layoutmenu.startAnimation(ScaleAnimation);


                    selecttable = 3;
                }


            }
        });




















    }

    /**
     * Manipulates the map once available.
     * This callback is triggered when the map is ready to be used.
     * This is where we can add markers or lines, add listeners or move the camera. In this case,
     * we just add a marker near Sydney, Australia.
     * If Google Play services is not installed on the device, the user will be prompted to install
     * it inside the SupportMapFragment. This method will only be triggered once the user has
     * installed Google Play services and returned to the app.
     */
    @Override
    public void onMapReady(GoogleMap googleMap) {
        mMap = googleMap;

        // Add a marker in Sydney and move the camera
        LatLng sydney = new LatLng(-34, 151);
        mMap.addMarker(new MarkerOptions().position(sydney).title("Marker in Sydney"));
        mMap.moveCamera(CameraUpdateFactory.newLatLng(sydney));

    }
}
