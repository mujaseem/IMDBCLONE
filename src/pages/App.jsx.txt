import { Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import MoviePage from "./pages/MoviePage";
import FavoritesPage from "./pages/FavoritesPage";

const App = () => {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/movie/:id" element={<MoviePage />} />
      <Route path="/favorites" element={<FavoritesPage />} />
    </Routes>
  );
};

export default App;
