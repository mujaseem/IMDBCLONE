import { useEffect, useState } from "react";
import { useParams } from "react-router-dom";

const MovieDetails = () => {
  const { id } = useParams();
  const [movie, setMovie] = useState(null);

  useEffect(() => {
    fetch(`https://www.omdbapi.com/?apikey=8d9d8cfe&i=${id}`)
      .then((response) => response.json())
      .then((data) => setMovie(data))
      .catch((error) => console.error("Error fetching movie details:", error));
  }, [id]);

  return movie ? (
    <div className="container">
      <h2>{movie.Title}</h2>
      <img src={movie.Poster} alt={movie.Title} />
      <p>{movie.Plot}</p>
      <p><strong>Year:</strong> {movie.Year}</p>
      <p><strong>IMDB Rating:</strong> {movie.imdbRating}</p>
    </div>
  ) : (
    <p>Loading...</p>
  );
};

export default MovieDetails;
